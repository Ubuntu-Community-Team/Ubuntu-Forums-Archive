---
title: "Hi! Started using UBUNTU again after some years."
date: 2020-01-16
forum: General Help
---

### Post by xcfstarflight1 on 2020-01-16
Hi! Just some things I am wondering about. 
I have my own local user account that i use for general purpose stuff and one that I have as a user configuring the system,
adding updated, packs and applications. 

1. ABOUT Ubuntuforum.org: Will I receive e-mails with answers, if not how do I set it up?
2. Should I make my used account non-administrator.
3. Will all my settings made with the administrator account apply to all users. If not, what do I need to do,
3.1 I want to configure settings made to the docking on the side to all users etc.. Where are settings for what
is for the user and what is for all users? 

Don't ask too much, just some pointers or any ideas, suggestions or direct input is good. Thanks!

---

### Post by crip720 on 2020-01-16
If you post a question and go to bottom of page there will be a small box asking how you want to be notify.  You should also list what version and desktop you are using.

---

### Post by Frogs Hair on 2020-01-16
> [COLOR=#000000]1. ABOUT Ubuntuforum.org: Will I receive e-mails with answers, if not how do I set it up?[/COLOR] If you subscribe to a thread from the thread tools notification options will be offered in a drop-down menu including email.

---

### Post by yancek on 2020-01-16
I'm not clear on what you are asking about your user/administrator account.  It is not possible to install and have a functioning Ubuntu system without creating one user.  That will be your primary user and that user will have administrator rights (using sudo).  You can create additional user and give them additional rights.  What settings are you referring to?

---

### Post by oldrocker99 on 2020-01-16
2.The user account should be in the sudoers group, which is default, and I **strongly** advise that you do *not* have a root user account. 

Having 2 accounts, one administrator and one user is extremely useful for the few savvy Windows users who do that, but it is unnecessary to do that with a Linux system.

2 and 3. Program settings in one account are all in that user's /home folder, nowhere else.

I hope that clears things up for you.

---

### Post by xcfstarflight1 on 2020-01-16
Just wondering how to see the version number in terminal? I dunno remembero xD

---

### Post by howefield on 2020-01-16
```
cat /etc/*-release
```

---

### Post by xcfstarflight1 on 2020-01-16
The terminal command for changing user policy. Administrator / regular user.

---

### Post by xcfstarflight1 on 2020-01-16
Thanks xD

---

### Post by xcfstarflight1 on 2020-01-19
[B]IMPORTANT:
[/B]Guys who has replied to this thread!
I cannot post any threads on "General" channel. I wrote a large importent for my work related business
forward and it all got deleted even now on "New to UBUNTU" channel.. Why? 
I will ask the questions here in this thread and hope someone can answer me to assist me further.

1. I cannot seem to find any good vim command sheet, vim book or a book of commands.
When i do a :!save is it saved in a special location besides the one the terminal window has open with the path whre i issued the command?
And if this is wrong procedure can someone tell me how to save and specify the path of where the file is going to be saved?
If someone has additional extra information like, vim sheets but most important a sheet of all common VIM commands?

2. If this message board dont accept like 5 messages pr week or something like that, I have been thinking about ASK UBUNTU.
Can someone please tell me in short what that is? Also, when I tried to sign in to some account, I cannot remember whitch web side i visited.
But anyway,  I could log in with Ubuntu Anywhere. 

So there are two questions about this actually. 
Can someone tell me if ubuntuforms.com,  ASK UBUNTU and the Ubuntu anywhere are connected? And even further if someone will help my company
grow, like in size of resources for information, are there any UBUNTU online features someone care to share and tell something about? 

Thank you so much guys you are so catchy with how things work. Hope i get to post this addition to my thread and not get "Forbidden 404" whitch
brings me to another question.. What port is 404 (if it is a port? i thought so) well, how does it work and what is it? A protocol? Simple explaination would 
be fine..

Hope you bared through with me and follow this thread you kind people!

---

### Post by Frogs Hair on 2020-01-19
> [COLOR=#000000]Can someone tell me if ubuntuforms.com, ASK UBUNTU and the Ubuntu anywhere are connected? And even further if someone will help my company[/COLOR]
[COLOR=#000000]grow, like in size of resources for information, are there any UBUNTU online features someone care to share and tell something about?[/COLOR]

Both Ubuntu Forums and ask Ubuntu are hosted by Canonical though this forum predates Ask Ubuntu and they include many of the same volunteers providing support. Canonical  does offer Ubuntu professional support.  [https://ubuntu.com/support](https://ubuntu.com/support)

---

### Post by coffeecat on 2020-01-19
> **xcfstarflight1 said:**
> I cannot post any threads on "General" channel. I wrote a large importent for my work related business
forward and it all got deleted even now on "New to UBUNTU" channel.. Why?

There is nothing in your profile preventing you from starting new threads in General Help or on the New to Ubuntu sub-forums, or in most of the other sub-forums. I don't know what you mean by channels. Do you mean sub-forums?

Just go to the sub-forum of your choice and click on the Post New Thread button to start a new thread. New to Ubuntu is here - [https://ubuntuforums.org/forumdisplay.php?f=326](https://ubuntuforums.org/forumdisplay.php?f=326) - and the Post New thread button is the big orange one on the left.

---

### Post by HermanAB on 2020-01-19
404 means that the http web server could not find the requested file.

---

