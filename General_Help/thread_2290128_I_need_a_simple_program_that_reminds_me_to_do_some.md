---
title: "I need a simple program that reminds me to do something twice a week"
date: 2015-08-09
forum: General Help
---

### Post by michael-piziak on 2015-08-09
Ubuntu 12.04 LTS user here.

I need a simple, easy to use, program that reminds me to do something [make a phone call] twice a week at a specific time on 2 different same specific days every week.

I would really like a program that I can tell it to remind me at a specific day and hour and minute each time.

Please make suggestions.

---

### Post by NathanRodriguez on 2015-08-09
I can suggest editing your crontab file to alert you at that specified time, something like that for 12:30 at days 0 and 4 (sunday and thursday):

29 0 * * 0,4 zenity --info --text="Thats time folks!"

You may need put zenity alerter command between quotes.

---

### Post by michael-piziak on 2015-08-09
Thanks for your suggestion,
but I'd prefer a program that does it - with no editing any files.
So I humbly ask for more suggestions.

---

### Post by tgalati4 on 2015-08-09
A [cronjob]("https://help.ubuntu.com/community/CronHowto") or use the *at* command if you have an irregular schedule that may not be suitable for *cron*.

```
notify-send -u critical "Phone Call" "Please call Jim."
```

---

### Post by michael-piziak on 2015-08-09
I may go with cronjob if I can't find a simple GUI program that I can click to start.  I'd like a program that I don't have to use terminal to start or give instruction to though.   Something like a simple GUI program.

---

### Post by michael-piziak on 2015-08-09
p.s. If I install cronjob, can you guys on here help me tell it which days and times I need to make the same phone call twice a week on 2 separate days (the days of the week and times on each day stay the same weekly).

---

### Post by vasa1 on 2015-08-09
> **tgalati4 said:**
> A [cronjob]("https://help.ubuntu.com/community/CronHowto") or use the *at* command if you have an irregular schedule that may not be suitable for *cron*.
...
Thanks for *at*!

Won't [gnome-schedule]("http://askubuntu.com/a/498698/") provide the GUI?

---

### Post by deadflowr on 2015-08-10
If you use Thunderbird, you can setup the lightning calendar add-on and create reminders with it.
Those reminders will show notification boxes for any event or task you schedule, when you schedule them.

---

### Post by yancek on 2015-08-10
Another option.

[https://apps.ubuntu.com/cat/applications/lucid/alarm-clock-applet/](https://apps.ubuntu.com/cat/applications/lucid/alarm-clock-applet/)

---

### Post by tea for one on 2015-08-10
If you use Firefox, you could add ReminderFox.

Here is the info:- [https://addons.mozilla.org/en-US/firefox/addon/reminderfox/](https://addons.mozilla.org/en-US/firefox/addon/reminderfox/)

---

### Post by tgalati4 on 2015-08-10
What are the exact days and times that you want the reminders?  Then we can create the cron entries.  Cron is already installed.

---

### Post by CantankRus on 2015-08-10
....and another option with a Unity panel indicator.
[http://bhdouglass.com/remindor/](http://bhdouglass.com/remindor/)

---

### Post by michael-piziak on 2015-08-12
> **deadflowr said:**
> If you use Thunderbird, you can setup the lightning calendar add-on and create reminders with it.
Those reminders will show notification boxes for any event or task you schedule, when you schedule them.

I may try this route.  Because I use Thunderbird the most.
But can I tell it to remind me at a specific time on specific days of the week?

In the below screenshot, which of the top 2 lightning calendar options would you suggest I install ?

---

### Post by michael-piziak on 2015-08-12
> **tgalati4 said:**
> What are the exact days and times that you want the reminders?  Then we can create the cron entries.  Cron is already installed.

ok, this sounds good.

I need it to remind me to "call girls at 6:30pm every Sunday."  Perhaps tell it to remind me at 5:45pm every Sunday.

Also, I need it to remind me to "text girls at 8:00pm every Wednesday." Perhaps tell it to remind me to do so at 7:45pm every Wednesday.

p.s. How will it remind me ?

---

### Post by tgalati4 on 2015-08-13
Open a terminal:

```
crontab -e
```

Choose *nano* (option 2).

Use the arrow key and scroll down to the bottom of the file and add the following: (Type carefully! or cut and paste with Control-C and Control-Shift-V)

```
 45 17 * * 0 DISPLAY=:0  notify-send -u critical "Don't Forget" "Call the Girls at 6:30 pm."
 45 19 * * 3 DISPLAY=:0  notify-send -u critical "Don't Forget" "Text the Girls at 8 pm."
```

Now, Control-O (and Enter) to save the file.
Control-Q to quit.

To list your current *cron* table ([crontab]("https://help.ubuntu.com/community/CronHowto"))

```
crontab -l
```

The notifications will pop up in the upper right corner and remain there for a few seconds.  Try it:

```
notify-send -u critical "Don't Forget" "Call the Girls at 6:30 pm."
```

This may need some tweaking to work.

---

### Post by michael-piziak on 2015-08-13
ok, sounds easy enough
Where does it store the file - in case I want to delete the file and start over
?

Update:  I don't think I pulled it off, see my screenshot of my terminal & what I tried below:

---

### Post by Hadaka on 2015-08-13
Hi,IMO the editor GEDIT works very well with CRONTAB
to allow the use of GEDIT with CRONTAB set gedit as crontab's
default editor. with this command.. It only needs to be done one time.
```
 echo "export EDITOR=gedit" | sudo tee -a .bashrc
```
boot
then open a terminal  crl/alt/t and do,,,
```
crontab -e
``` and enter the 2 lines of code tgalati4 wrote out for you
see screen shot
[ATTACH=CONFIG]263840[/ATTACH]
click save and exit.  THAT'S IT !
open a terminal ctrl/alt t and test with..
```
notify-send -u critical "Don't Forget" "Call the Girls at 6:30 pm."
```

*To remove gedit as crontab's default editor..
```
sudo sed -i '/^export EDITOR=gedit/ d' .bashrc
```

---

### Post by tgalati4 on 2015-08-13
You need to choose Option 2 (nano) as the editor.  That was your issue.  Or simply hit (Enter) since [2] is showing as the default pick.

To remove a crontab, use:

```
crontab -r
```

When using Linux, you need to follow instructions carefully.

---

### Post by michael-piziak on 2015-08-15
> **tgalati4 said:**
> You need to choose Option 2 (nano) as the editor.  That was your issue.  Or simply hit (Enter) since [2] is showing as the default pick.

To remove a crontab, use:

```
crontab -r
```

When using Linux, you need to follow instructions carefully.


I don't know what happened, but now when I put "[COLOR=#000000][FONT=Ubuntu Mono]crontab -e" into terminal - now I get a totally different looking screen than I got previously.

[/FONT][/COLOR]See what I get now in this screenshot

---

### Post by Hadaka on 2015-08-15
That is the nano editor that tgalati4 directed you to use.
follow his instructions in post # 15.....pay attention,follow direction,read carefully
and dont forget to ...Control-O (and Enter) to save the file. and then Control-Q to quit
thats the crtrl key ctrl/o ctrl/q. AFTER you enter your 2 lines of data that tgalati4 wrote
out for you. 
good luck.

---

