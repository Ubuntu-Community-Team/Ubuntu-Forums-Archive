---
title: "Open ubuntu 12.04 without password."
date: 2015-10-03
forum: General Help
---

### Post by waltwin on 2015-10-03
I am embarrassed to ask this question again but I know that someone out there can tell me how to open ubuntu 12.04 without entering my password. I did receive one suggestion but it was  unsuccessful. I have selected automatic login  in user accounts but but my password is still requested. It worked when I was using 12.04 before and 14.04 until I experienced a system malfunction and had to reload 12.04. Any help will be much appreciated.

waltwin

---

### Post by zvacet on 2015-10-04
As far as  I know there is no need for password if you autologin. You will have to make changes in file 

```
/etc/lightdm/lightdm.conf
```


 You have explained procedure [here]("https://wiki.ubuntu.com/LightDM").

---

### Post by waltwin on 2015-10-05
Thank you for your response. I have been unsuccessful in attempting to make this work. I know I am doing something wrong because anything I enter responds, command not found.

waltwin

---

### Post by slickymaster on 2015-10-05
To enable auto login just edit the **/etc/lightdm/lightdm.conf** file, as zvacet suggested, and add the following lines replacing USERNAME with your own username:
```
autologin-user=USERNAME
autologin-user-timeout=0
```Save and close the file.

---

### Post by Rick St. George on 2015-10-05
What is not mentioned is HOW you edit a file. I believe this is what you want.

VIM has many advanced features such as syntax  highlighting (a feature that color codes key words in programming  languages and configuration files).  If you prefer a more feature-packed  text editor than nano and the rest, this is a good one. To use vim to edit a file, do the following in a terminal, where  'filename' is the name of the file you want to create or modify:
```
 vim filename 
```

For more info;
[https://askubuntu.com/questions/474312/how-to-edit-files-in-a-terminal-with-vim](https://askubuntu.com/questions/474312/how-to-edit-files-in-a-terminal-with-vim)

---

### Post by slickymaster on 2015-10-05
> **Rick St. George said:**
> What is not mentioned is HOW you edit a file. I believe this is what you want.

VIM has many advanced features such as syntax  highlighting (a feature that color codes key words in programming  languages and configuration files).  If you prefer a more feature-packed  text editor than nano and the rest, this is a good one. To use vim to edit a file, do the following in a terminal, where  'filename' is the name of the file you want to create or modify:
```
 vim filename 
```

For more info;
[https://askubuntu.com/questions/474312/how-to-edit-files-in-a-terminal-with-vim](https://askubuntu.com/questions/474312/how-to-edit-files-in-a-terminal-with-vim)

Right, right. My bad :p

Or, for a simpler text editor approach, go with nano```
sudo nano /etc/lightdm/lightdm.conf
```

---

### Post by grahammechanical on 2015-10-05
Did you by any chance install Ubuntu and choose to have an encypted home folder?

---

### Post by waltwin on 2015-10-06
When I enter /etc/lightdm/lightdm.conf I get a "access denied" response. It would aooear that I just know enough to enter these commands. I think that entering my pass word will have to do. Your responce is appreciated.

waltwin

Let me try that again. When I enter "/etc/lightdm.conf" I get a "access denied"response. It would appear that that I just don't know enough to use these commands. I think that entering my password will have to do. Your response is much appreciated.

waltwin

I received the following information after entering "sudo nano /etc/lightdm/lightdm.conf":
```
[SeatDefaults]
autologin-guest=false
autologin-user=watwin
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=unity-greeter
user-session=ubuntu
```
I am unable to understand what the problem is!

waltwin

---

### Post by slickymaster on 2015-10-06
> **waltwin said:**
> I received the following information after entering "sudo nano /etc/lightdm/lightdm.conf":
```
[SeatDefaults]
autologin-guest=false
autologin-user=**[SIZE=3][COLOR=#ff0000]watwin[/COLOR][/SIZE]**
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=unity-greeter
user-session=ubuntu
```
I am unable to understand what the problem is!

waltwin
Your lightdm.conf file seems to be correct for what you want. The thing that comes to mind is your username, is it really watwin, or is it waltwin like the one you have in the forums?

---

### Post by waltwin on 2015-10-06
No, I did not select that option.

waltwin is the name I selected when asked for my user name at install.

---

### Post by slickymaster on 2015-10-07
Can you please open a terminal window and run the following command```
whoami
```and post back here the output you get.

---

