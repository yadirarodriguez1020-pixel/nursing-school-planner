# 🌟 Nursing School Planner - Feature Guide

## Overview
This document provides detailed information about each feature in your Nursing School Planner App.

---

## 1. 📊 Dashboard

**Purpose**: Your central hub for all metrics and progress tracking.

### Key Components:
- **GPA Summary**: Overall GPA, semester GPA, trend indicator
- **Assignment Status**: Total assignments, completed, overdue
- **Clinical Hours**: Total hours logged, hours this month, progress toward requirement
- **Exam Readiness**: Exams coming up, study progress %, weak areas
- **Habit Completion**: This week's habit completion rate, trends
- **Self-Care Hours**: Monthly self-care hours, recommendations

### Formulas Used:
- `=AVERAGE(Grade Tracker!B:B)` - Calculate overall GPA
- `=COUNTIF(Assignments!D:D,"Completed")` - Count completed assignments
- `=SUMIF(Clinical Log!A:A,">=TODAY()-30",Hours Column)` - Last 30 days of clinical hours

---

## 2. 📅 Calendar

**Purpose**: Visual management of all important dates and events.

### Features:
- **Event Types**: Assignments Due, Exams, Classes, Clinical Shifts, Study Blocks, Deadlines
- **Color Coding**: Different colors for each event type
- **Quick View**: Hover over dates for event details
- **Sync Capability**: Links to relevant sheets (can show assignment details, exam info, etc.)
- **Month/Week Toggle**: Switch between calendar views

### Integration Points:
- Pulls assignment due dates from Assignments sheet
- Pulls exam dates from Exam Tracker
- Pulls clinical shifts from Clinical Log
- Pulls class times from Class Schedule

---

## 3. 📈 Grade Tracker

**Purpose**: Monitor all course grades with advanced calculations.

### Columns:
| Column | Purpose |
|--------|---------|
| Course Name | Name of the class |
| Current Grade % | Percentage or letter grade |
| Grade Points | Numeric value for GPA calc |
| Credits | Course credit hours |
| Weight | How much it counts toward GPA |
| Letter Grade | A, B, C, D, F |
| Semester | Which semester/term |

### Formatting:
- **Conditional Formatting**: Green (90+), Yellow (80-89), Red (<80)
- **Weighted GPA**: `=SUMPRODUCT(Grade Points, Credits)/SUM(Credits)`
- **Letter Grade Conversion**: 90-100=A, 80-89=B, 70-79=C, 60-69=D, <60=F

---

## 4. 📝 Assignments

**Purpose**: Track all assignments from start to submission.

### Columns:
| Column | Purpose |
|--------|---------|
| Assignment Name | What is it? |
| Course/Subject | Which class? |
| Due Date | When is it due? |
| Status | Not Started / In Progress / Completed |
| Priority | High / Medium / Low |
| Grade % | If graded, what's the score? |
| Notes | Additional details |
| Days Until Due | Calculated (TODAY - Due Date) |

### Formulas:
- **Overdue Counter**: `=COUNTIF(Due Date, "<TODAY()")`
- **Grade Auto-calc**: Average of all assignment grades
- **Color Code Status**: Red if overdue, Yellow if due soon, Green if complete

### Conditional Formatting Rules:
- Red: Status = "Not Started" AND Due Date < TODAY()
- Yellow: Due Date between TODAY() and TODAY()+7
- Green: Status = "Completed"

---

## 5. 🏥 Clinical Log

**Purpose**: Comprehensive record of all clinical experiences.

### Columns:
| Column | Purpose |
|--------|---------|
| Date | Date of shift |
| Time | Start/End time |
| Preceptor Name | Who supervised you |
| Unit/Department | Where were you? |
| Patient Count | How many patients? |
| Patient Types | Medical, Surgical, ICU, etc. |
| Skills Practiced | List of skills used |
| Procedures | Any procedures performed/observed |
| Reflections | What did you learn? |
| Hours Worked | Total hours (auto-calculated) |
| Confidence Level | 1-5 scale |

### Features:
- **50+ Session Rows**: Ample space for all clinical experiences
- **Hours Calculation**: `=HOUR(End Time - Start Time)`
- **Skill Tracking**: Links to Skills Checklist for updating mastery levels
- **Reflection Prompts**: What went well? What could improve? What did you learn?

---

## 6. ✅ Skills Checklist

**Purpose**: Track mastery of essential nursing skills.

### Columns:
| Column | Purpose |
|--------|---------|
| Skill Name | Name of the skill |
| Category | Assessment, Medication, Vitals, Wound Care, etc. |
| Status | Not Started / In Progress / Mastered |
| Date First Practiced | When you first did it |
| Times Practiced | How many times? |
| Confidence Level | 1-5 scale |
| Last Practiced | Most recent date |
| Notes | Any observations |

### 40+ Skills Include:
- Vital Signs Assessment
- IV Insertion
- Catheterization
- Medication Administration
- Wound Dressing
- Patient Hygiene
- Bed Bath
- Catheter Care
- Foley Management
- Blood Draw (Venipuncture)
- NG Tube Insertion
- Suctioning
- Tracheostomy Care
- Chest Tube Management
- EKG Placement
- Blood Pressure Monitoring
- Blood Glucose Monitoring
- Pain Assessment
- SOAP Charting
- Report Giving
- And 20+ more!

### Mastery Tracking:
- **Not Started**: Haven't done it yet
- **In Progress**: Practiced 1-3 times, building confidence
- **Mastered**: Practiced 4+ times, confident performing independently

---

## 7. 📚 NCLEX Prep

**Purpose**: Track NCLEX study progress with accuracy metrics.

### Columns:
| Column | Purpose |
|--------|---------|
| Category | Pharmacology, Med-Surg, Peds, OB, etc. |
| Topic | Specific topic within category |
| Question Number | Question ID |
| Difficulty | Easy / Medium / Hard |
| Correct/Incorrect | C or I |
| Time Spent (min) | How long did you take? |
| Rationale Notes | Why was this the answer? |
| Date Practiced | When you did this |

### Formulas:
- **Accuracy by Category**: `=COUNTIF(Category & Correct)/COUNTIF(Category)*100`
- **Weak Areas**: Categories with <70% accuracy
- **Time Analysis**: Average time per question by difficulty

### Category Sidebar:
- Pharmacology: __% accuracy
- Medical-Surgical: __% accuracy
- Pediatrics: __% accuracy
- Obstetrics: __% accuracy
- Psychiatric: __% accuracy
- Adult Health: __% accuracy

---

## 8. 📅 Weekly Planner

**Purpose**: Time management and weekly scheduling.

### Structure:
```
Time Slots (Monday - Sunday)
6:00 AM
7:00 AM
8:00 AM
... (30-min or 1-hour increments)
10:00 PM
```

### Color Key Legend:
- 🟦 **Blue**: Class/Lecture
- 🟩 **Green**: Study/Study Group
- 🟪 **Purple**: Personal/Family Time
- 🟥 **Red**: Clinical Shift
- 🟨 **Yellow**: Work
- ⬜ **White**: Free Time

### Features:
- **Block Planning**: Set study blocks for each subject
- **Clinical Shifts**: Mark your shift times
- **Class Schedule**: Auto-populate from Class Schedule sheet
- **Break Times**: Mark meals and breaks
- **Time Tracking**: Review how you spent your week

---

## 9. 🧪 Exam Tracker

**Purpose**: Prepare for and monitor exam performance.

### Columns:
| Column | Purpose |
|--------|---------|
| Exam Name | Exam 1, Midterm, Final, etc. |
| Course | Which class? |
| Date | When is the exam? |
| Days Until Exam | Countdown (TODAY - Exam Date) |
| Study Progress % | How much have you studied? |
| Topics to Review | List of topics |
| Practice Test Scores | Your scores on practice tests |
| Target Score | What do you want to get? |
| Actual Score | Your final score (after exam) |
| Study Materials | Links/references |
| Study Time Hours | Total hours spent studying |

### Features:
- **Countdown Timer**: Days remaining until exam
- **Progress Tracking**: % of material studied
- **Practice Test Integration**: Track multiple practice attempts
- **Score Prediction**: Based on practice tests
- **Study Plan**: Topics and time allocation

---

## 10. 📊 Habit Tracker

**Purpose**: Build consistency with daily habits for wellness and success.

### Columns:
| Column | Purpose |
|--------|---------|
| Habit | Exercise, Sleep 8hrs, Meditate, Journal, etc. |
| Category | Health / Wellness / Academic |
| Mon | ✓ or X |
| Tue | ✓ or X |
| Wed | ✓ or X |
| Thu | ✓ or X |
| Fri | ✓ or X |
| Sat | ✓ or X |
| Sun | ✓ or X |
| Weekly % | Completion percentage |
| Streak | Current streak count |

### Sample Habits:
**Health Category:**
- Exercise (30 min+)
- Sleep 8+ hours
- Drink 8 glasses of water
- Eat 5+ servings of fruits/veggies
- Stretch/Yoga

**Wellness Category:**
- Meditate (10 min)
- Journal (5 min)
- Take breaks
- Walk outside
- Connect with friends/family

**Academic Category:**
- Review class notes
- Practice questions
- Read assigned chapters
- Attend all classes
- Study group

### Formulas:
- **Weekly %**: `=COUNTIF(Mon:Sun,"✓")/7*100`
- **Streak**: Count consecutive weeks at 100%

---

## 11. 💆 Self-Care Log

**Purpose**: Prioritize wellness and mental health during nursing school.

### Columns:
| Column | Purpose |
|--------|---------|
| Date | When? |
| Time | What time? |
| Activity Type | Sleep, Exercise, Meditation, Social, etc. |
| Duration (min) | How long? |
| Mood Before | 1-10 scale |
| Mood After | 1-10 scale |
| Mood Improvement | After - Before |
| Energy Before | Low / Medium / High |
| Energy After | Low / Medium / High |
| Notes | How did it feel? |

### Activity Types:
- 😴 **Sleep**: Extra nap, good night's sleep
- 🏃 **Exercise**: Workout, walk, yoga, sports
- 🧘 **Meditation**: Mindfulness, breathing exercises
- 👥 **Social**: Time with friends, family, loved ones
- 🎨 **Creative**: Art, music, hobbies, crafts
- 📚 **Learning**: Reading for pleasure, podcast, TED talk
- 🍽️ **Nutrition**: Healthy meal, cooking, meal prep
- 🛁 **Pampering**: Bath, massage, spa, skincare
- 🌳 **Nature**: Park, garden, outdoor time
- 🎬 **Entertainment**: Movie, show, comedy

### Formulas:
- **Monthly Hours**: `=SUM(Duration)/60` for current month
- **Mood Average**: Average of all "Mood After" scores
- **Most Effective Activity**: Type with highest mood improvement

---

## 12. 🎓 Class Schedule

**Purpose**: Organize and reference all course information.

### Columns:
| Column | Purpose |
|--------|---------|
| Course Name | Full name of the course |
| Course Code | CN 101, etc. |
| Meeting Days | M/W/F, T/Th, etc. |
| Meeting Times | 9:00-10:30 AM |
| Location | Room number, building |
| Instructor Name | Professor/Instructor name |
| Instructor Email | Contact email |
| Office Hours | When can you meet? |
| Office Location | Where is office? |
| Phone Number | Instructor contact |
| Credits | How many credit hours? |
| Prerequisites | What's needed to take this? |
| Required Materials | Textbooks, supplies |
| Grading Breakdown | Participation 10%, Exams 40%, etc. |
| Notes | Important info |

### Features:
- **Quick Reference**: All course info in one place
- **Contact Info**: Easy access to instructor details
- **Schedule Integration**: Auto-populates Weekly Planner
- **Calendar Integration**: Shows class times on calendar
- **Grading Breakdown**: Know how your grade is calculated

---

## 🔄 How Features Work Together

```
Class Schedule
     ↓
Weekly Planner (pulls class times)
     ↓
Assignments (track assignments from each class)
     ↓
Grade Tracker (monitor grades in each class)
     ↓
Dashboard (see overall GPA from Grade Tracker)

Clinical Log
     ↓
Skills Checklist (update skills after clinical)
     ↓
Dashboard (see clinical hours completed)

Exam Tracker
     ↓
Calendar (shows exam dates)
     ↓
NCLEX Prep (if preparing for NCLEX)
     ↓
Dashboard (shows exam readiness)

Habit Tracker + Self-Care Log
     ↓
Dashboard (shows wellness metrics)
```

---

## 💪 Success Tips

1. **Update Daily**: Spend 5-10 minutes updating your planner each day
2. **Review Weekly**: Every Sunday, review the week and plan the next one
3. **Use Colors**: Stick to the color-coding system consistently
4. **Set Realistic Goals**: Don't overwhelm yourself with too many habits
5. **Celebrate Wins**: Mark celebrations in your calendar
6. **Adjust as Needed**: The system should work for YOU, not the other way around
7. **Backup Regularly**: If using digital sheets, back up your data

---

**You are capable of success in nursing school! Use this planner as your guide. 🎓💪**
