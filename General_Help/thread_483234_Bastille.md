---
title: "Bastille"
date: 2007-06-24
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2007-06-24
Ok, I'm really obsessed with security. Which is why I came over to linux in the first place. I can't stand thinking about people getting into my stuff and corrupting it. I wanted a locked system that I could still access the internet with and so I did some (a lot) of research and came upon this Bastille program. I installed it and went through the questionaire and set it. Everything seemed to be working fine until reboot. I AM the administrator but not root of course and well... when I went to log in I got a message that said "The system admin has temporarily disabled access to the system." So I booted directly into the terminal to change the settings back to default and it did nothing. I don't want to uninstall it because the settings might still be there. Anything else I can do? I am 2 weeks into linux and still learning. Sorry if this is a moronic mistake. :(

---

### Post by Sin@Sin-Sacrifice on 2007-06-24
Well... with no help I finally figured it out with a little outside-the-box thinking. I saw a few forums that talked about user accounts and finally saw one that talked about setting them from the terminal. If you happen to fall into this trap then just edit the access.conf file so that not just the root user is able to log in. Do this by rebooting into the root terminal or as it was so called in the boot selection "Ubuntu version.something (Recovery)" in stead of the normal boot GUI. This is kind of like Microsoft's safe boot mode except without the pretty GUI.  This will load everything but only in the terminal and you will be logged in as root. From there you can nano /etc/security/access.conf and just add your account in the lines next to root It'll look kind of like this: 

# Disallow non-root logins on tty1
#
#-:ALL EXCEPT root YOURACCOUNTHERE:tty1
# 
# Disallow console logins to all but a few accounts.
#
#-:ALL EXCEPT wheel shutdown sync:LOCAL
#
# Disallow non-local logins to privileged accounts (group wheel).
#
#-:wheel:ALL EXCEPT LOCAL .win.tue.nl
#
# Some accounts are not allowed to login from anywhere:
#
#-:wsbscaro wsbsecr wsbspac wsbsym wscosor wstaiwde:ALL
#
# All other accounts are allowed to login from anywhere.
#
-:ALL EXCEPT root YOURACCOUNTHEREALSO:LOCAL

ctrl-x, y to say yes and enter to confirm. Type reboot and start normally. You will now have access with whatever account you added to the lines. **little side note. If you're not dual -booting with another OS. You might not get a choice as to how you boot. When you restart the computer hit Esc until you see the list of boot modes. Such as recovery mode. Otherwise you'll just keep rebooting into normal. I am dual-booting with bista so I almost forgot to add that.

---

