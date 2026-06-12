---
title: "Finance hates passwords..."
date: 2007-05-21
forum: General Help
---

### Post by Madmoose on 2007-05-21
Hello, 

I was wondering if there is a way to make it so that you don't need to enter a password to do everything on Ubuntu. I was finally able to get her switched over from windows, but after about the fourth time she had to enter her password she was getting annoyed. I told her that even in the new vista they are getting so that you have to do the same thing, and Vista is even more in your face then anything I've ever seen. 

Now, 

She really likes Ubuntu, but she is thinking about going back to XP. All because she has to keep entering her password. I have it so it will log in, and not ask for her user name and password, but I she doesn't want to have to enter it all. 

I told her I didn't think there was a thing I could check to make it so she didn't have to, and she said "You're telling me these Geeks can make a whole OS, but can't make a button that will turn off the need to enter passwords?" I told her that "it's what the public wants, and the public is very security needy. You are just one person calling for something that many others want." She said "It's open source ain't it? I they could do what ever they want with it. I want that button. Go ask! Now...."

Anyway, 

Any idea's?

---

### Post by kaamos on 2007-05-21
Use autologin for gdm and set [this](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29)

---

### Post by Hellcom on 2007-05-21
Your fiance/fiancee must doing a lot regular admin changes if he/she is required to enter a password so often. Well as far as I know "sudo" and its equivalents are a fundamental part of security on ubuntu and other distros, which has proved so effective that even vista has "borrowed" it :P So turning off this feature is not generally advised as it is inherently insecure, which explains why there is no "button" to turn off passwords.

However, if you really insist set autologin to GDM and:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29)

---

### Post by Rinzwind on 2007-05-21
Is your marriage going the be alot like this? :popcorn:

What does she DO that requires passwords alot?

I can think of a few:
- At some point synaptic and add/remove programs should not be used anymore: all the software that is needed is installed. Those 2 tend ask for your password every time.
- Next is 'updates': asks pwd every time it's used. 
- Login: can be circumvented as shown above this post. 

But what else is there for her!? 
Is it the wireless applet?

---

### Post by Madmoose on 2007-05-21
You're right. As some point when you install all the software you're going to use you don't need to enter anymore passwords. Though, I think she is talking about the updates and the occasional chance she wants to install some new item. I believe she just wants to click install updates and/or install software, and call it a day. Not have to spend the extra 2 seconds in enter her password. 
I'm just do what I'm told. :p

Anyway, thanks to everyone that posted. I'll try out the info you shared. 


Moose.

---

### Post by hessiess on 2007-05-21
just set your pasword to somthing close to the enter key like "#" or "/"  or "]" !!!!!

---

