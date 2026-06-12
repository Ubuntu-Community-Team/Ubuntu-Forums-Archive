---
title: "No mail notification for gnome?"
date: 2006-12-05
forum: General Help
---

### Post by bigblop on 2006-12-05
Hi I use Ubuntu 6.10 with gnome and would like to get an email notifier in the taskbar. I have tried installing mail notification but that program makes no sense.

When I get a new mail another window opens with some info. But afterward I have to manually open my mail reader. I would also like the notification to stay in the taskbar, I don't see any reason for opening a seperate window for the info.

Is there some mail notification software that will dock into the gnome taskbar and when I click on it my mail program opens? I should just show the number of new incoming mails and when I have read them it should automatically set the counter to 0.

gnubiff almost does this, besides I have to manually reset the new mail counter after having read my messages which does not make any sense.

---

### Post by 23meg on 2006-12-05
> 
When I get a new mail another window opens with some info. You can disable the summary popup in the preferences. > But afterward I have to manually open my mail reader.You can also set it up so that it will open your mail program with a click.> I should just show the number of new incoming mails and when I have read them it should automatically set the counter to 0.This is the only thing it can't do; however, if you hover your cursor on the icon, you'll get a summary indicating how many mails you have.

---

### Post by bigblop on 2006-12-05
I have tried selecting 'open mail reader' under the option click but nothing happens.

If I disable the big window that appears how should I then know that I have received any mail?

Could be nice if I could add the program to the taskbar instead and a number would only appear over the icon in the taskbar

---

### Post by 23meg on 2006-12-05
> I have tried selecting 'open mail reader' under the option click but nothing happens.It should open your mail reader; make sure you have one selected in System / Preferences / Preferred Applications.> If I disable the big window that appears how should I then know that I have received any mail?By hovering your cursor over the tray icon, or by unchecking "Always display" in the "Status Icon" tab; with the latter, the icon will only appear in the tray if you have new mail. 

Also, if you find the popup too intrusive, you can make it smaller and / or appear for a shorter period.> Could be nice if I could add the program to the taskbar insteadIf you want its icon to appear all the time, check "Always display". It will change according to whether you have any new mail.

---

### Post by bigblop on 2006-12-06
I have now added mail notification to the taskbar. But when I click it nothing happens.

I have then from the system menu choosen mail notification which gives me the settings menu for mail notification.

In this menu I have choosen to remove the check in "Always display" I have also choosen to remove the check in "Enable mail summary popup" in the "mail summery popup" pane.

But after closing the settings menu the icon is still in the taskbar, and nothing happens when I get new mail.

What is wrong with this program?

---

### Post by bradleyd on 2006-12-06
don't add launcher to gnome panel. When you launch it from menu "Internet" it will add mail icon in system tray. Without the popup it will only tell you how many messages in your inbox. If you right click on tray icon tit will say main window. click that now you have Main window listing emails from, subject, etc.. what email provider are you using? Do you want something that will popup a window with from subject and date when a new message arrives?

---

### Post by bigblop on 2006-12-06
That is the problem, when I launch it from internet it does NOT appear in the taskbar. For some reason gnome taskbar does not show the mail-notification. I guess this is some bug in either gnome or mail-notification.

It works fine on my laptop so I guess that the notification area is malfunctioning for some reason on my regular PC, any ideas on what might be causing this?

I use a pop account (yahoo) but have also tried using my gmail account but its the same.

I use thunderbird as my mail reader.

---

### Post by bradleyd on 2006-12-06
I had a similar problem, but I needed notification when new email arrived. I use evolution, and wrote a little app that displays new email. It uses a filter in evolution and pipes the email to the app.

---

### Post by Rodneyck on 2006-12-06
Use my favorite gnome application, gnubiff. You can set him to check several types of email accounts and if you tweak the customization it will play sounds and the linux penguin (not set by default) jumps up and down in the task bar to notify me.

[http://gnubiff.sourceforge.net/](http://gnubiff.sourceforge.net/)

Here is a how-to I sent another user regarding the set-up procedure:

1. Add gnubiff in your taskbar.
2. right click on it and select "preferences".
3. In the mailboxes there may be a generic one listed, if so highlight and hit "properties". If not, then hit he "add" button and call it whatever, then hit the properties button to open it up.
4. In the "types" field, pull down the menu and select "POP."
5. In the address field, for yahoo, enter the server info, which is "pop.xxxxx.com" or whatever your email provider gives you .
6. Enter your user name and password in the next two fields.
7. pull down the "details" and make sure "autoselect" is listed so it will detect all the other information.

That should do it!

The other two things I changed was listed under the "applet or Bif" tab, select any audio file you want to use to notifiy when mail is received. I also changed under "When New Mail" in the "show image" field the icon there to the one that makes him jump up and down when you have new mail. On my system, I entered this in the field, "/usr/share/gnubiff/tux-jump(64x64).png"

---

### Post by bigblop on 2006-12-06
I have tried gnubiff, the problem is that after I have read my mail I manually have to clear the number of new mail found by gnubiff. It does not automatically reset the new mail counter after I have read my mail.

I have now got mail-notification to run on my laptop (the notification area is gone on my regular PC and I cannot seem to get it back) but eventhough I have removed the check in "Always display" the icon is still in the notification area. Guess this is a bug. Seems there is no working email notification for gnome.


I am thinking of using KDE instead there it works perfect, seems that gnome is still a bit behind KDE.

---

### Post by Rodneyck on 2006-12-06
> **bigblop said:**
> I have tried gnubiff, the problem is that after I have read my mail I manually have to clear the number of new mail found by gnubiff. It does not automatically reset the new mail counter after I have read my mail.



Strange, I have never had this problem. I know it depends on how much time you set between checking for new mail. I set mine for 1 minute, so it clears the mail counter pretty quickly.  However, the default is like 10 minutes I think, so it would not clear it until 10 minutes later when it checks again. That could be your problem.

---

### Post by bigblop on 2006-12-06
> **23meg said:**
> It should open your mail reader; make sure you have one selected in System / Preferences / Preferred Applications.By hovering your cursor over the tray icon, or by unchecking "Always display" in the "Status Icon" tab; with the latter, the icon will only appear in the tray if you have new mail. 

Also, if you find the popup too intrusive, you can make it smaller and / or appear for a shorter period.If you want its icon to appear all the time, check "Always display". It will change according to whether you have any new mail.

I have now tried to uncheck "Always display" but it keeps apearing eventhough  I have read all new incoming mail.

I have then tried to check "Always display" but when I get new mail nothing happens with the icon. I had hoped for some basic change of icon color or sound, but there is pratically no notification at all.

---

### Post by bigblop on 2006-12-06
> **Rodneyck said:**
> Strange, I have never had this problem. I know it depends on how much time you set between checking for new mail. I set mine for 1 minute, so it clears the mail counter pretty quickly.  However, the default is like 10 minutes I think, so it would not clear it until 10 minutes later when it checks again. That could be your problem.


I have set the delay interval to 10 seconds but the new mail count never gets reset before I manually rightclick on it and choose "mark mailboxes read"...makes no sense.

---

### Post by Rodneyck on 2006-12-06
Just to check, there are two dely settings. The one you want is sort of hidden. You have to pull up the "properties" of each account and click on the "details". Under that change the time to minutes or seconds.

If that does not help, sorry man.

---

### Post by bigblop on 2006-12-06
jep that is where I have set it to 10 seconds.

---

### Post by davidbdr on 2007-06-14
This drove me nuts too until I figured out the obvious correction  to the problem.

1. Click the Mail-Notification icon in System/Preferences

2. The Mail Notification settings will open.

3. Click on "Status Icon" tab

4. select under **General** "always display"

This was one of those "duh" moments I seem to have frequently.  :tongue:

I see that someone already figured this out but was still having problems with the implementation.

---

### Post by dav9000 on 2007-06-15
Did you try cGmail? It supports both gmail and pop3 accounts and has some other pretty features.

Check it out in [http://cgmail.tuxfamily.org/](http://cgmail.tuxfamily.org/)

---

### Post by davidbdr on 2007-06-15
Thanks for the heads up. I'll have to check it out.

---

