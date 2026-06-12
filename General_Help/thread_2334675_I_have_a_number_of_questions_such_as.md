---
title: "I have a number of questions such as:"
date: 2016-08-21
forum: General Help
---

### Post by wjbradley on 2016-08-21
When the compute is left to idle, the screen goes black and when I restart it it asks for my password. I have lost the original password and would like to stop it asking me for a password.

Everything was working OK and when I logged off. Restarted and a flag came up telling me I had a problem. Great! it did not say what.

Went to use email and it would not work, when I checked the network it told me that I am "out of range". Go figure, I have not moved and the laptop beside me connected perfectly.

Any help would be appreciated. I am using Ubuntu 14.04 :)

Bill

---

### Post by banceu_sergiu_ione on 2016-08-21
Hi

If you go to system settings / brightness & lock, you can unselect at bottom ' require my password when....' and then switch Lock to off.

For network try reboot once more and see if it work back.

Do you think you can remember back your password, cuz you may need it.

Try open a terminal and type ```
 su 
``` this will try to log in as admin, Try it till you get your password back, just in case if you still have a clue of it.

---

### Post by Impavidus on 2016-08-21
This tutorial teaches how to reset your password: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by wjbradley on 2016-08-21
> **banceu_sergiu_ione said:**
> Hi

If you go to system settings / brightness & lock, you can unselect at bottom ' require my password when....' and then switch Lock to off.

For network try reboot once more and see if it work back.

Do you think you can remember back your password, cuz you may need it.

Try open a terminal and type ```
 su 
``` this will try to log in as admin, Try it till you get your password back, just in case if you still have a clue of it.

Thank you for  your reply. I was able to stop the password request from poppling up.

When I clicked on the wi-fi indicator in the top bar it told me that my wi-fi was cut of by a switch. Don't know what that switch or where to look for it.

I deleted the terminal button from the side menu, to bring another one up. Now I can't figure out how to get the terminal.

Thank you again.

---

### Post by banceu_sergiu_ione on 2016-08-21
When you click on the wi-fi, is ' enable network ' and ' enable wi-fi ' selected? if not select them and wait to see if you get connected back.

If you can not see ' Enable Network ' go open System Settings  click on Network and check if the Airplane Mode (top right ) is on to off. If is on then switch it off. Check again now if you can see the ' Enable Network' on wifi indicator, make sure it is selected, as well as the Enable WiFi.

---

### Post by Frogs Hair on 2016-08-21
ctrl +alt + t will open the terminal. Once on the launcher you can lock it and open a new instance of the terminal by right clicking if needed.

---

### Post by grahammechanical on 2016-08-21
"Button" & "Icon" mean different things to us. It causes confusion.

How did you get a Terminal icon in the launcher in the first place? It is not put there by default. We open the Dash. Click the Ubuntu icon at the top of the launcher or tap the flying Windows key (called super key in Linux). That will open the Dash and search for Terminal. Then click the icon to load the terminal. Its icon will appear in the launcher. Right click the icon and select "Lock to Launcher" to put the icon there all the time. Or, not if you want to load the terminal from the Dash each time.

If this machine is a laptop then a certain keyboard combination will turn off the WiFi adapter to save battery power. If the machine has Windows installed and we turn off WiFi in Windows then it is likely that WiFi will remain off when we load Ubuntu.

We can also put Ubuntu into Airplane mode. That will turn off the WiFi adapter. We can also use the drop down Network Manager icon to disable WiFi or Networking. Both will stop the WiFi adapter from working.

You will need to know your user password. You will need it at some point in the future. Most system updates do not require authentication. But certain updates, such as security fixes for the Linux kernel, will require authentication by your user password. As this is clearly a recent installation of Ubuntu you should think about re-installing and this time make a note of the password that you will be required to set during the installation process.

Regards

---

