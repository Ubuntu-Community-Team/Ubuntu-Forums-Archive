---
title: "I hate it when stuff just doesn't work"
date: 2007-01-05
forum: General Help
---

### Post by sleepytom on 2007-01-05
So I've switched from Windows to Ubuntu Linux in part because Windows was bogging down and taking too long to switch tasks, etc.. But after a couple of weeks of using Ubuntu, there are some maddening tasks that don't seem to work right. Maybe somebody can help me figure these things out:

1. Session startup: I'd like devilspie to open near the beginning of my Window session, so I go to System > Preferences > Sessions and click on the "Current Session" tab. highlight devilspie and change the Order to 10. I then click "Apply" and "Close". But when I sign out and log back on, the Order for devilspie is back to 50. How can I fix that.

2. Copying addresses into Thunderbird: I thought I'd give Thunderbird a try because of the reputation of the mail filter. So I installed it and tried without success to copy my addresses over from Microsoft Outlook and from Outlook Express. First I tried a .csv that I made in Outlook before switching to Linux, but the values would not import correctly. So I went to my virtual machine Windows, imported my old addresses into Outlook Express, installed Thunderbird (windows), imported address from Express, then exported mail from Thunderbird in .ldif format. I then switched back to Ubuntu, opened Thunderbird then Addresses > Import > Text File ; then I selected the .ldif file and.... nothing. Thunderbird just sits there doing nothing. The "next" button is grayed out and I'm forced to select "Cancel". Maddening.

I suppose everything else is working well. I've had good success burning CDs, which were frequently failing in Windows. But can anybody help me with these couple of problems?

Thanks

---

### Post by stanthecaddy22 on 2007-01-05
> **sleepytom said:**
> So I've switched from Windows to Ubuntu Linux in part because Windows was bogging down and taking too long to switch tasks, etc.. But after a couple of weeks of using Ubuntu, there are some maddening tasks that don't seem to work right. Maybe somebody can help me figure these things out:

1. Session startup: I'd like devilspie to open near the beginning of my Window session, so I go to System > Preferences > Sessions and click on the "Current Session" tab. highlight devilspie and change the Order to 10. I then click "Apply" and "Close". But when I sign out and log back on, the Order for devilspie is back to 50. How can I fix that.

2. Copying addresses into Thunderbird: I thought I'd give Thunderbird a try because of the reputation of the mail filter. So I installed it and tried without success to copy my addresses over from Microsoft Outlook and from Outlook Express. First I tried a .csv that I made in Outlook before switching to Linux, but the values would not import correctly. So I went to my virtual machine Windows, imported my old addresses into Outlook Express, installed Thunderbird (windows), imported address from Express, then exported mail from Thunderbird in .ldif format. I then switched back to Ubuntu, opened Thunderbird then Addresses > Import > Text File ; then I selected the .ldif file and.... nothing. Thunderbird just sits there doing nothing. The "next" button is grayed out and I'm forced to select "Cancel". Maddening.

I suppose everything else is working well. I've had good success burning CDs, which were frequently failing in Windows. But can anybody help me with these couple of problems?

Thanks


1. If you want it to start automatically when you log in put it under the next tab, "startup programs". I'm not too familiar on setting the startup order however so sorry I can't help out further.

2. Go ahead and use the csv just make sure when you export it you only select the fields that you use for your contacts.
-In thunderbird open the address book, then tools > import; choose
 Address Books; Text File; and locate the csv file you have created.
-This screen is very important! make sure the top checkbox about the first record containing field names is checked
-In the box below, use the move up/down to line up the Record data fields on the right with the imported fields from the csv on the left. For example 'Primary Email' should line up to 'Email Address' and if you use that field the box should be checked.
- Uncheck all the boxes in the address book fields that you are not importing.
-click ok and that name of the address book should be listed in your address books and you can move the contacts to wherever you desire.

Hope this helps!
Gavin

---

### Post by koenn on 2007-01-05
>  I hate it when stuff just doesn't work
who doesn't ....


here's another way to copy a complete firefox and thunderbird confiiguration from Wondows to Ubuntu - since you've already imported outlook to thunderbird, it should be a walk in the park
[http://users.telenet.be/mydotcom/howto/linux/migration01.htm](http://users.telenet.be/mydotcom/howto/linux/migration01.htm)

---

### Post by sleepytom on 2007-01-05
> **koenn said:**
> 
here's another way to copy a complete firefox and thunderbird confiiguration from Wondows to Ubuntu - since you've already imported outlook to thunderbird, it should be a walk in the park
[http://users.telenet.be/mydotcom/howto/linux/migration01.htm](http://users.telenet.be/mydotcom/howto/linux/migration01.htm)

Ahh, yes. That was an easy fix indeed. Copying the profile over worked perfectly. Thanks a lot.

---

