---
title: "computer wont start up with out entering setup"
date: 2007-09-02
forum: General Help
---

### Post by lilbluegremlin on 2007-09-02
hey all, 
so here is the problem.
every time i start up my computer it stops loading after checking for the main processor and then i have to either enter setup or the boot menu. once i go into one of those and then exit it loads ok for a while and then stops again when it check for the floppy disk. if i press f1 it continues to load fine and then asks me what kernel i want to use. after that it goes on fine. i was wondering if there is some way i could skip all that or just the first part because it takes so long for the computer to tell i have hit delete or f11
or is this just normal ubuntu/linux behavior?

thank you for your time.
~Erik

---

### Post by southernman on 2007-09-02
It has nothing to do with Ubuntu... period.

It's your bios(s) boot order, quick boot being disabled also maybe.

edited - also check that the date (day, month, year, and time) are all set right. If you cleared your CMOS recently, this could be ONE of the reasons your getting this, if the boot order is set right.

---

### Post by lilbluegremlin on 2007-09-02
ok cool, so anyone have any suggestions on fixing that. i'm afraid my dos/terminal understanding is limited.

---

### Post by southernman on 2007-09-02
Well, it's pretty intuitive once you enter setup. Just a mattter of tabbing through the options using page up/page down, +/-, enter and page up/page down to change items usually.

Enter setup and read the guide at the bottom of the screen. It will tell you how to do all that. As you tab through, either with the tab key or arrow up/arrow down, there will usually be a brief description of what that item does.

If your unsure what something does and how it will effect your system, leave it the heck alone... or you could have more serious problems on your hands.

What you should really focus on for now is the "boot" tab on top of the page, and finding your date/time settings (usually on the first page when entering setup.

*trembles for you as I submit this reply*

---

### Post by lilbluegremlin on 2007-09-02
ok thanks i fund the date and time in the cmos and they were already correct. i looked around a little in the other menus and did not see anything that looked like it had to do with start up.
thank you for your help.
~Erik

---

