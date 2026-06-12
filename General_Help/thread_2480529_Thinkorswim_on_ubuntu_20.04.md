---
title: "Thinkorswim on ubuntu 20.04"
date: 2022-11-01
forum: General Help
---

### Post by twjohnson13 on 2022-11-01
I am attempting to run thinkorswim stock charts on Ubuntu 20.04. I have the program installed on my machine but the wizard did not create a shortcut for me. On the website How 2 shout there was a procedure for creating a desktop short cut. First instruction was " [COLOR=#202124]wget [https://www.how2shout.com/linux/wp-content/uploads/2021/07/thinklogo.png](https://www.how2shout.com/linux/wp-content/uploads/2021/07/thinklogo.png)[/COLOR] .  Second instruction was "[COLOR=#202124]sudo mv thinklogo.png /opt/thinkorswim/" [/COLOR][SIZE=2][COLOR=#202124]When I install this command I receive an error that it can not perform the function because it is not a directory. Any help would be greatly appreciated. I had the original install working but when I close it the application will not restart. I am not savvy enough to start it without a shortcut. [/COLOR][/SIZE]

---

### Post by Perfect Storm on 2022-11-02
Hello,

Make sure that you executing the commands in the right directory.
```
cd
wget https://www.how2shout.com/linux/wp-content/uploads/2021/07/thinklogo.png
sudo mv thinklogo.png /opt/thinkorswim/

```

---

### Post by twjohnson13 on 2022-11-03
I know just enough to be dangerous. Seriously. I hate to ask for help if I have not done my due diligence. I understand the basics of the Ubuntu software or computers in general. I understand that CD before the commands I installed in the terminal refers to change directory.  But I am confused on what I am attempting to do here. It looks like I went to a website and grabbed a graphic; the thinkorswim logo ?? I assume this will be my icon for the shortcut ?? Then I attempted to move it to something connected to thinkorswim in the computer file system ?? If I am in the terminal; which I am barely comfortable with; do I need to be working in a particular directory ?? And what directory should I be in ?? Thank you for your time !! I am sure these are very basic concepts but I do not understand.

---

### Post by Perfect Storm on 2022-11-04
> ? I assume this will be my icon for the shortcut ?? Then I attempted to move it to something connected to thinkorswim in the computer file system ??
correct.
> do I need to be working in a particular directory ?? And what directory should I be in 
If the icon you downloaded via the command you gave it should be in the directory you executed the wget command.

---

### Post by twjohnson13 on 2022-11-07
Thank you so much Mr. Storm. I was still confused after your reply; but I schooled myself on directories, as you were guiding me to this being a potential issue. Took a couple of days of reading to understand them better. Looks like I had an issue with the wizard during installation. It may of been me hitting buttons without understanding the results; but I found the installation located in the /usr/local directory. The code I was attempting to use later instructed to send to the /opt/ directory. I read what /opt/ was; and realized what was going on. This may seem very basic for someone that is familiar with the Ubuntu operating system; but this took me days to understand. Thank you so much for the help; without your guidance; I would still be attempting to reload again and again; not knowing which should be my next move.

Tom J

---

### Post by Perfect Storm on 2022-11-07
Glad you solved it :)

---

