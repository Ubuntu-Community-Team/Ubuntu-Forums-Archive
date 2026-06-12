---
title: "Skype problem - seems to be running for the very first time every time started"
date: 2013-03-21
forum: General Help
---

### Post by orbital on 2013-03-21
I'm running Ubuntu 12.04 and I recently installed Skype using the Ubuntu Software Center. Everything seems to be working ok, except that everytime I start Skype, I have to agree to Terms of Use ja Skype fails to remember my sign-in details. It's like I'm running Skype every time for the very first time. Any ideas how to fix this annoying problem? As another question, what is the best software for voice/video calls that supports both Ubuntu desktop and Android mobile devices? Thanks for any help and ideas in advance.

---

### Post by guimaster on 2013-04-13
> **orbital said:**
> I'm running Ubuntu 12.04 and I recently installed Skype using the Ubuntu Software Center. Everything seems to be working ok, except that everytime I start Skype, I have to agree to Terms of Use ja Skype fails to remember my sign-in details. It's like I'm running Skype every time for the very first time. Any ideas how to fix this annoying problem? As another question, what is the best software for voice/video calls that supports both Ubuntu desktop and Android mobile devices? Thanks for any help and ideas in advance.

I began experiencing this problem on Kubuntu 12.04 tonight. The solution was easy:

#1 - Close out Skype
#2 - Delete the .skype folder from the Home folder (show hidden files and folders)
#3 - Re-open Skype

Now I'm back to normal.

---

### Post by scbingham on 2013-04-13
Guimaster's fix worked for me :)

Now to see if Skype keeps crashing when contacts log on or off whilst I'm talking or typing to someone else...

---

### Post by ascmartins on 2013-04-20
Hi. I had same issue. I read your post, and try to figure out what was the problem. Because I didn't want to lose chat history I went inside the .Skype folder and notice that there was a file called 'shared.xml' with restricted privileges, write was not allowed. So I went to terminal an changed file permissions:
**sudo chmod 777 /home/<user-name>/.Skype/shared.xml**

So far it works. And I'm back to normal with my chats history there...

regards...

---

