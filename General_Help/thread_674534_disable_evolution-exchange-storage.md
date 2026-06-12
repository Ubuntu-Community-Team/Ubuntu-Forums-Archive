---
title: "disable evolution-exchange-storage"
date: 2008-01-21
forum: General Help
---

### Post by High_Yield on 2008-01-21
OK guys... many posts about this but nobody knows how to do it...

Using the "up-to-the-minute" Ubuntu Gutsy 7.1, ...

How do you stop the evolution-exchange-storage service from running at startup ?

:confused:

---

### Post by erpo on 2008-01-22
First of all, it's not 7.1. It's 7.10. The 7 is for the year 2007 and the 10 is for the 10th month of that year (October). Lots of Linux projects have this numbering convention (stretching the minor version numbers and patchlevels into double digits) and it bugged the heck out of me when I first switched from Windows. You'll get used to it.

evolution-exchange-storage is not running on my 7.10 system, so I can't tell you how it's being started. I would look under Ubuntu Menu->System->Preferences->Sessions in the Startup Programs tab for a start.

---

### Post by High_Yield on 2008-01-22
Hey erpo-

Thanks for the smart-alek first paragraph and near worthless response second paragraph.

Would anyone who:
a) is not a techie wanna-be
b) actually knows something about ubuntu/evolution
... please reply ?

Detail..
- I don't wish to tinker with "session-saving", I would like to know where/how it gets loaded in the first place and stop it
- The package should not be "deleted" as I may want to test the Exchange functionality later (doubtful but...)

Thanks in advance - B

---

### Post by crosswalker21 on 2008-02-29
Preliminary note: High_Yield: Be nice!  Ubuntu is all about community, sharing and kindness.  erpo was trying to be helpful and explain some background to help you.  Consider the fact that he (or she, I'm new here) didn't have to help you, but did so out of a spirit of servitude and community that deserves everyone's respect, including mine and yours.

That said, I'll try to answer your original question, if you'll try to be a little more compassionate and less short-tempered.  It may take me a while as I'm fairly new to Ubuntu and I have a reasonably full life, but I'll give it a shot.  Expect an answer soon.

**Update: The answer**
This worked for me:
Step 1 - Open up the system monitor (on standard Ubuntu with Gnome you can run it from the terminal by entering ```
gnome-system-monitor

```
Step 2 - Find the evolution-exchange-storage process, right click it and select kill process.
Step 3 - open up terminal again and enter the following.
```
sudo apt-get purge evolution-exchange
```
Step 4 - Restart your system (this might only require a logout, but I haven't tested that scenario)

I know you said that you'd rather not delete the package, but, until someone else can answer your question, this method works.  On the upside, you'll use approximately 1.3MB less disk space.  If you ever need to re-install the exchange functionality, just open up terminal and type: ```
sudo apt-get install evolution-exchange
```

Hope this helps!:)

---

