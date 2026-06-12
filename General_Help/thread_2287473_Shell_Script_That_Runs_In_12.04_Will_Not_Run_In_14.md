---
title: "Shell Script That Runs In 12.04 Will Not Run In 14.04"
date: 2015-07-19
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-07-19
Hello,

Shell Script That Runs In 12.04 Will Not Run In 14.04

Thanks, Hannibal

---

### Post by QIII on 2015-07-19
Hello.

Again:  What is the failure behavior?  What messages are you getting from the terminal?  Text of the script?

I don't know about others here, but my crystal ball is in the repair shop.

---

### Post by coljohnhannibalsmith on 2015-07-20
Sorry,

I was in the middle of build and added my list of problems to the forum without sufficient detail.  This probably should have gone in my notebook first.

Symptoms:

No terminal output.  The script just opens with gedit.  When I go into properties and select Open With I don't get an option for BASH and no option to Browse.

When I try: bash -x /home/sophie/script-name it runs fine.

Thanks, Hannibal

---

### Post by yancek on 2015-07-20
I would first check to see that the file is set as executable if it is opening in gedit.

---

### Post by Vaphell on 2015-07-20
also check in the file browser preferences
There is a Behavior tab with relevant checkboxes: executable text files should be opened with text editor on click, executable text files should be executed on click, ask every time.

---

### Post by coljohnhannibalsmith on 2015-07-20
It was the behavior tab!

Thanks, Hannibal

---

