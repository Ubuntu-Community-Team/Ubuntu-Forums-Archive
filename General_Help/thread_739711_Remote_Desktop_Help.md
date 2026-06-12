---
title: "Remote Desktop Help???"
date: 2008-03-30
forum: General Help
---

### Post by Blacklife08 on 2008-03-30
I am very new to ubuntu, and have no idea how to use Remote Desktop.  (didnt know when i was using windows either)  

Can someone show me, or point me in a direction to find out please?
thanks!

---

### Post by Blacklife08 on 2008-03-30
I actualy solved my own problem here.  However i have another related question.  

How can i open a remote desktop Of Windows XP on my ubuntu computer?

Thanks again!

---

### Post by pointone on 2008-03-30
I've actually been meaning to set this up myself for a while. Let's see if I can't walk both of us through it...

1) On the Windows machine, open **Control Panel > Performance and Maintenance > System**, and open the **Remote **tab. Check "Allow users to connect remotely to this computer". Take note of the "Full computer name" shown immediately below this checkbox. Click **Select Remote Users** and make sure your user is listed (if your user is a member of the Administrators group, then it already has access), then click apply.

2) Your Windows account must be password-protected in order to use Remote Desktop. If it already is (you are required to enter a password while logging in), then skip this step. Otherwise, open **Control Panel > User Accounts > Change an account** and select your account on the Windows machine. Click "Create a password" and follow the instructions. ***Make sure you use a STRONG PASSWORD***. No birthdays, common names, simple words, etc. A mixture of numbers both upper- and lower-case letters is recommended, at least 5 characters long. Remote Desktop allows FULL access to your system--you want to ensure your system is secure.

3) Let's test it out! On your Ubuntu machine, open **Applications > Internet > Terminal Server Client**. Under "Computer", enter the "Full computer name" of the Windows machine found in step 1. Under "User Name" and "Password", enter the username and password of your Windows account. This should be all that's required if your home network isn't too complicated. Click **Connect**.

A new window should appear with a Windows login prompt. If not, we may have to play around a bit more.

You can fiddle with the Terminal Server Client settings to change the default resolution, enable sound, and improve performance. If you want to access this computer away from home, this will require some kind of DMZ/port forwarding setup on your router.

---

