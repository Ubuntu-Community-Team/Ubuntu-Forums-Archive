---
title: "New User Login Issues"
date: 2007-02-18
forum: General Help
---

### Post by brentaserio on 2007-02-18
Hello Everyone:

I'm new to the forums, and linux. I am trying to teach myself a little about linux prior to taking my required courses for my degree. I literally just installed ubuntu, during the installation process it had asked me to set my password, which I set as Heyheyhey1 and verified the password once more, and continued the installatino. Now, I have read that the login at default is set as:

User: Root
Pass: Heyheyhey1 (This is what I entered during installation process.)

After installation was complete, I was ready for first login. It asked me for user so i typed
root then asked me for password I typed Heyheyhey1. After several attempts at loging in I figured I would ask you all what Ubuntu sets the default user name login.

1. How do I acquire the login name ubuntu had set for me?

Any help would be greatly appriciated.

---

### Post by taurus on 2007-02-18
Did you really create a root account during the installing process?  There is already a root account and it is locked as a default.  Therefore, you are not supposed to use root as your login name.  Try picking something else like john or mike or whatever.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by brentaserio on 2007-02-18
No I didn't create a profile during installation process. It just asked me to enter a password and verify it. I did. So I am assuming the password it had me enter was for the user profile. I just typed int he password twice it didn't tell me or ask me for user profile. But in the gui of ubuntu its like windows it asks for Username, which I didn't enter nor do i know what it is and a password. I can't enter just password. It requires username but i dont know what it is.

---

### Post by Maestro23 on 2007-02-18
What version are you running? How did you install it?

---

### Post by brentaserio on 2007-02-18
Um I think 6 which is the newest one i downloaded from ubun's website. Burned it to dvd 3.46gb and booted from disc after creating partition and installed. How do i find out which user name to use since it didn't ask me to create one.

---

### Post by taurus on 2007-02-18
Sounds to me like you installed the oem version then.  Therefore, your username is oem and your password is the one that you created during the installing process.  After you log in, don't forget to run this command to create an actual account for you to use from now on.

```
sudo oem-config-prepare
```

---

### Post by brentaserio on 2007-02-18
Where would i type this command i have gui installed.

---

### Post by taurus on 2007-02-18
After you log in, open a terminal, Applications -> Accessories -> Terminal, and type that command at the prompt.

```
sudo oem-config-prepare
```

---

### Post by brentaserio on 2007-02-18
Ok got It Great! Next challenge which I'm sure people have asked before. I am using laptop with broadcom wifi. Where should I start on this one to get it working?

I have configured lo already and enabled it still doesn't work. I'm guessing i need driver or windows emulator for this. I have no Idea where to start any direction would be great.

---

### Post by taurus on 2007-02-18
First, search for the exact model of your wireless card to see if it has already been answered and if you can't find it, create a new thread in the Networking and Wireless section.

---

### Post by Maestro23 on 2007-02-18
Some links for the OP to read/bookmark:

How to install in Ubuntu:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

*Ubuntu guide link is in my sig.

Good luck.

---

### Post by brentaserio on 2007-02-18
Will Do... Uhhh ohhhh..

ok i logged in with oem opened terminal typed

sudo oem-config-prepare, it asked me to restart so i did, brought up system configuration to create new user followed directions step 4 was to create user hit next/finish and it wouldnt do anything so i restarted brought it up again typed in my new user hit next still nothing, now i cant do anything or get to the regular login screen. What should i do?

---

### Post by taurus on 2007-02-18
What is the new of the new user that you try to add?

---

### Post by brentaserio on 2007-02-18
full name was Brent Serio
user login name was Anthrondo
password blah blah
next button, dead link

---

### Post by taurus on 2007-02-18
Is there any space in your password?

---

### Post by brentaserio on 2007-02-18
No, I would just use the oem login permanently but i can't get to that login screen cause the stupid system config keeps poping up on me lol I really appriciate your help

---

### Post by taurus on 2007-02-18
What if you use john as a username and johnny as a password.  See if that works.

---

### Post by brentaserio on 2007-02-18
Ok, I'll be back in a few minutes, i'll give it a shot

---

### Post by brentaserio on 2007-02-18
no luck

---

