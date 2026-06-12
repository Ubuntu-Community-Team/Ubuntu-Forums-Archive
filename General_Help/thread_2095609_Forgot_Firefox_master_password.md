---
title: "Forgot Firefox master password"
date: 2012-12-17
forum: General Help
---

### Post by PDA1 on 2012-12-17
I forgot my Firefox master password where all the passwords are stored.

Yes, I know about password re-set where everything is lost.

Is there a way to crack it?



If so...exactly how?

---

### Post by Cheesemill on 2012-12-17
A quick google for 'recover firefox master password linux' should give you what you need.

---

### Post by PDA1 on 2012-12-17
I've been doing that for the past 2 hours to no real success.

There's FiremasterLinux which is some program claiming it can help crack a FF password. However, there's no real documentation or installation instructions in using it in Linux.

Thus it's another one of those dud programs promising the world and delivering nothing.

---

### Post by lightning slinger on 2012-12-17
Try this! ;)

[http://support.mozilla.org/en-US/kb/reset-your-master-password-if-you-forgot-it](http://support.mozilla.org/en-US/kb/reset-your-master-password-if-you-forgot-it)

Dont think there is much else you can do!

---

### Post by Cheesemill on 2012-12-17
I agree. The easiest method is to reset your master password and then use the 'I've forgotten my password' link on all of the websites you had logins for to reset these passwords as well.

Even if you could find a program to crack the master password it would use a brute-force attack meaning it could well take years to recover your forgotten password.

---

### Post by PDA1 on 2012-12-17
> **lightning slinger said:**
> Try this! ;)

[http://support.mozilla.org/en-US/kb/reset-your-master-password-if-you-forgot-it](http://support.mozilla.org/en-US/kb/reset-your-master-password-if-you-forgot-it)

Dont think there is much else you can do!


You're joking...right?

**Warning: Resetting your master password will remove all of your saved usernames and passwords.**

---

### Post by PDA1 on 2012-12-17
> **Cheesemill said:**
> I agree. The easiest method is to reset your master password and then use the 'I've forgotten my password' link on all of the websites you had logins for to reset these passwords as well.

Even if you could find a program to crack the master password it would use a brute-force attack meaning it could well take years to recover your forgotten password.


My password for FF probably wasn't very original or complex.

I had hoped I could move the relevant files over to Windows and then do a crack on it using the Firemaster GUI. But, being basically lazy, I tried copying the stuff (key3.db and sigons-something-or-another) over to windows and the Firemaster program didn't think those were the right files.

Oh well.

---

### Post by mikewhatever on 2012-12-17
> **PDA1 said:**
> My password for FF probably wasn't very original or complex.

I had hoped I could move the relevant files over to Windows and then do a crack on it using the Firemaster GUI. But, being basically lazy, I tried copying the stuff (key3.db and sigons-something-or-another) over to windows and the Firemaster program didn't think those were the right files.

Oh well.

Out of curiousty, I've built Firemaster for Linux from source, and let it crack the test, 1234, password. It shufled through the passwords quickly, but found nothing. Not sure what's wrong with it, but it's probably safe to assume that Firemaster doesn't work.

---

### Post by PDA1 on 2012-12-17
That was my conclusion too- it doesn't work.

Anyone that writes a program for a certain os should provide clear and easy to understand examples on how to install and use the program. The firemaster program uses windows style examples (i.e. C:/blah/blah/blah) Which, for a dunce like myself, promotes zero confidence in the program's author. 

Everyone can find some program that supposedly will crack or try to crack a forgotten password but most of those program user instructions are written in techno-geek language that a casual user will not be able to understand.

---

### Post by slixz85 on 2012-12-17
did a quick scan through here cant believe no one just suggested remove firefox and configurations that should do it. "sudo apt-get purge firefox" then to make sure open synaptic and check under the residual config tab to make sure it is uninstalled from there as well.

of course you will lost all your info but oh well. just remember it next time. quick fix

---

### Post by PDA1 on 2012-12-17
Getting rid of Firefox and passwords is NOT what I'm trying to accomplish.

I want to discover what my forgotten password is.

---

### Post by slixz85 on 2012-12-17
> **PDA1 said:**
> Getting rid of Firefox and passwords is NOT what I'm trying to accomplish.

I want to discover what my forgotten password is.

I believe i gotta say good luck. I searched around google pretty well and I know good ways of typin searches. it appears it is just an added security feature of firefox's etc because that would mean anyone could reset your firefox password that use your computer if they wanted and see your passwords cause all they would have to click is show passwords after they made a new password for your firefox. who knows it may not be impossible but i bet it will take you some time. if you find this out let us know

---

### Post by mikewhatever on 2012-12-18
I've tried the command line version of Firemaster for Windows (it doesn't require installation), and, surprisingly, it worked as expected. Perhaps it's not that bad after all. The Linux version was supposed to be a port, it is very old (2010), and looks abandoned.

You can learn how to use it from [http://securityxploded.com/firemasterlinux.php](http://securityxploded.com/firemasterlinux.php). Let me know if something is unclear.

---

