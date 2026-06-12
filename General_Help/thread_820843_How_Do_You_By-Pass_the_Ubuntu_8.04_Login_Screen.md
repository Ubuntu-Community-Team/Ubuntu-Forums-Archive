---
title: "How Do You By-Pass the Ubuntu 8.04 Login Screen"
date: 2008-06-06
forum: General Help
---

### Post by Ashejoe on 2008-06-06
Can someone tell me how to by-pass the madatory "user name / password" screen that pops up every time I boot into Ubuntu 8.04 so that I can just get straight to the desktop without having to log-in each time ?

All the searches I've done for instructions appear to describe how to do it in earlier versions of Ubuntu, (like 6 & 7), but 8.04 does not seem to follow the same protocol ???

I live alone and don't share a computer with anyone else.  For me, it's more of a nuciance than anything else.

Thank You

Joe Ashe

---

### Post by briandu on 2008-06-06
OK under /system/admin/login window

and enable

u sure u want to do this?

---

### Post by Ashejoe on 2008-06-06
thanks Briandu..... I sincerely appreciate your suggestion.  I'll give it a try here in a minute.  But again, thank you.

Not being a smart-alec, but sincerely, why would a person like me need to password protect access to a computer that only "I" use ?  (remember, I live alone and don't share my computer with anyone else.)  Perhaps there's something I don't realize ??

---

### Post by WeEatVista on 2008-06-06
You never know, I mean what if a thief came in and wanted to check his e-mail or something. He would be blocked by the dreaded log in screen and you would ruin his day =D

---

### Post by briandu on 2008-06-06
not so much the thief but nobody comes there - no privacy required of course - then OK but I do not believe that. Your choice after all 

Cheers

---

### Post by geirha on 2008-06-06
If a "thief" sees the login screen, he could just boot into recovery mode to get root access. Autologin doesn't really make the system any less secure.

---

### Post by ColTom2 on 2008-06-06
Thanks for asking this question and thanks for the answer!

---

### Post by Ashejoe on 2008-06-06
I attempted to do what you said briandu, but, it didn't work in Ubuntu 8.04.  

I did notice that your suggestions is the way to eliminate the log-in user name / password in Ubuntu SEVEN.  But as I mentioned, version 8.04 of Ubuntu appears to be different. 

For example, as you stated I went in to;  SYSTEM --> ADMINISTRATION --> LOGIN WINDOW.  That brought a pop-up screen with six tabs along the top as you can see in the jpg attached.  The one that appeared to make the most sense, (as well as the only one that said "ENABLE")  was the SECURITY tab.  As you can see, I did "enable" it.

Yet, when I rebooted, it brought me right back to the "enter user name / password" security screen. 

Ubuntu 8.04 has something different in the way you by-pass the log in screen.  I just can't figure it out.  All I know, is that (for me), it's very annoying.

---

### Post by johnl on 2008-06-06
It looks like you need to select your username in the combo box right under the checkbox that you checked --  you need to tell Ubuntu which user you want to automatically login.

---

### Post by Ashejoe on 2008-06-07
Thanks johnl.  That "appears" to have done the trick... I think.....

During 3 reboots I was no longer asked my "user name".  However, it did require me to enter something called a "KEYRING"  (or something like that) password before allowing me access to the Ubuntu 8.04 desktop.  

Interestingly, on the 4th, and subsequent reboots, I went directly to my desktop without having to enter any user name or password.  That's exactly what I wanted to do.

So again, I thank you for taking the time to help me.  I sincerely appreciate ALL of the *sincere* responses I received to my inquiry.

I'll tell you, the more I use Ubuntu 8.04, the more I really like it.  Over the years, I've dabbled on and off with Mepis, Mandrake, SuSe and a number of lesser known Linux distributions.  (mostly out of curiosity)  But I must admit, Ubuntu and the folks on the various forums have really made a believer out of me.

So again, thank you.

Joe Ashe
Hickory, NC

---

