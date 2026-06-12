---
title: "ubuntu gets the language wrong on dates"
date: 2015-04-27
forum: General Help
---

### Post by likes2skate on 2015-04-27
I was in Thailand when I installed kubuntu 14.04 on this laptop, but I chose US English as the system language.  

Despite the fact that I chose US English as the system language, when the system displays the date, it displays the Thai date using Thai script. Like this:

```

27 Apr 2015 
Current default time zone: 'America/New_York'
Local time is now:      &#3592;. 27 &#3648;&#3617;.&#3618;. 2558 08:20:55 EDT.

```

Note that on the Thai calendar, the year is 2558, not 2015.

Thai script is probably not installed on your computer, so the Thai script will probably not display properly, so I attach a screen shot.  Sometimes when I get a Thai date, the script does not display properly, and I get stars instead of Thai characters.

This is a problem using the terminal in kubuntu or when I go to a text session (Crtl-Alt-F1 to Crtl-Alt-F6).  This is never a problem using the graphical desktop environment.

In Settings, Local, the preferred language is American English.

How do I get the system to display US dates in English?

---

### Post by Vladlenin5000 on 2015-04-27
Language and locale (regional settings) are two different and independent settings. Check the second tab in language support and adjust accordingly.

---

### Post by likes2skate on 2015-10-18
On the language tab, language is set to American English only, see the screen shot.

I was mistaken, in addition to Thai script in the dates on the terminal, I also spotted Thai script in the GUI, see the attached screen shot.

I am on a different laptop, but I have not yet solved this problem.

---

### Post by likes2skate on 2015-10-21
Thai script is showing up in Skype now, see the screen shot.

I assume there is a ubuntu level setting that is allowing this, because in System Settings, the country is USA and the language is US English.

Helpful suggestions would be appreciated.

---

### Post by likes2skate on 2015-10-21
[ATTACH=CONFIG]265089[/ATTACH]Thai script is showing up in Skype now, see the screen shot.

I assume there is a ubuntu level setting that is allowing this, because in System Settings, the country is USA and the language is US English.

Helpful suggestions would be appreciated.

---

### Post by likes2skate on 2015-11-18
Steps to solve the problem can be found here:

[https://www.kubuntuforums.net/showthread.php?65711-getting-the-wrong-language-and-dates-in-Firefox-and-the-GIMP](https://www.kubuntuforums.net/showthread.php?65711-getting-the-wrong-language-and-dates-in-Firefox-and-the-GIMP)

---

