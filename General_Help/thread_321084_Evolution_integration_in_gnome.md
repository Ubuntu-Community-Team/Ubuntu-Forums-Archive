---
title: "Evolution integration in gnome?"
date: 2006-12-18
forum: General Help
---

### Post by QwUo173Hy on 2006-12-18
I've moved from kubuntu to Ubuntu just to try. One thing I miss is having mail notification in the system tray that kmail provided. I don't like having programs minimized when I'm not using them.

Thanks,
Jarlath

---

### Post by Spin Doctor on 2006-12-21
Look at the solution in this forum:

[http://ubuntuforums.org/showthread.php?p=1775648](http://ubuntuforums.org/showthread.php?p=1775648)

Let me know if it works, I have not had time to try it myself yet... =)

---

### Post by QwUo173Hy on 2006-12-22
Tried the first method and didn't like it. You have to execute the plugin seperately every time manually. I didn't try the other methods. It's just too much work for me at the moment.

I was a linux freak for a few years, but now I'm burned out and I just want simplicity! ;) 

Happy Christmas.

Jarlath

---

### Post by fragos on 2006-12-22
I run mail-notification and point it at my gmail box at Google.  After installing with Synaptic it starts on its own with every boot.  This was the default.  There are a number of notification options.  When mail is available an enveope displays in the notification area.  Resting the cursor on the icon displays a list of available emails.  I'm not sure how the version with "evolution" integration works but no email package needs to be running for this one to work.  I normally read email with Firefox but on occcasion run evolution.  I've configured gmail for pop access and evolution will retrieve available email.

---

### Post by QwUo173Hy on 2006-12-23
I've just tried that Fragos and it works really really well.

First I ran
```
mail-notification -p
```
to get the preferences up and configure my gmail account.

Now when I get mail, the little icon comes up in the status bar and if I click on it, it runs evolution. That is exactly what I wanted, thankyou!

To make a program such as this run at startup, you need to do

System -> Preferences -> Sessions -> Startup Programs -> Add

and then add the name of the program,  you want to start up when you log in...

But I found that mail-notification was already there so hopefully thats all that needs to be done.

Thanks again!
Jarlath

---

### Post by fragos on 2006-12-23
mail-notification places itself in the startup list so you don't have to.  They thought of everything.

You're welcome -- George

---

