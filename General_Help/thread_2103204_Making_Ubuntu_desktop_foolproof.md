---
title: "Making Ubuntu desktop foolproof?"
date: 2013-01-09
forum: General Help
---

### Post by blnl on 2013-01-09
Recently, I installed Ubuntu 12.04 for my mother that absolutely knows nothing about computers. She only knows how to use Firefox, Thunderbird and Skype.
Yet somehow (I have no clue hoe) she managed to mess up everything by changing the system language to some incomprehensible hieroglyphs (possibly Greek or Russian). She explained that she was trying to check the spelling in an eMail message.
It bothers me that in Ubuntu, a user can change any system settings using just his own user password. I would like to change this before my mother (by accident) deletes her user account.

I personally use Fedora, where you need root password for any system configuration change, which is different from the user password. I would like to have something like that in Ubuntu. A user password for my mother, which can't even change the clock time. And another password for myself that enables me to configure her user account settings.

What is the best/safe way to do that?

Is it enough if I enable root account and remove her from the sudoers?

---

### Post by sandyd on 2013-01-09
> **blnl said:**
> Recently, I installed Ubuntu 12.04 for my mother that absolutely knows nothing about computers. She only knows how to use Firefox, Thunderbird and Skype.
Yet somehow (I have no clue hoe) she managed to mess up everything by changing the system language to some incomprehensible hieroglyphs (possibly Greek or Russian). She explained that she was trying to check the spelling in an eMail message.
It bothers me that in Ubuntu, a user can change any system settings using just his own user password. I would like to change this before my mother (by accident) deletes her user account.

I personally use Fedora, where you need root password for any system configuration change, which is different from the user password. I would like to have something like that in Ubuntu. A user password for my mother, which can't even change the clock time. And another password for myself that enables me to configure her user account settings.

What is the best/safe way to do that?

Is it enough if I enable root account and remove her from the sudoers?
1. Create a new user in the 'sudo' group
2. Remove her from the 'sudo' group.
3. There are still ways to change the language, this is **account specific**, and not system-wide. I suggest you use a different UI where there is no config panel, such as openbox, or disable her access to the configuration panel itself.

I can think of something better though.
Backup every folder, including all the hidden .* folders in the home directory after removing her from the sudo group, and setting up an admin account as described above. Exclude .thunderbird, .mozilla, and other folders of applications she uses while she is not logged into her account in any way. On computer startup, create a script to copy the backed up folders to her account. This _has_ to be done only at computer startup, as some files cannot be replaced while she is logged in. When she screws up the computer, just restart it to fix everything.

You can also probably ask her to just use the Guest account as well.

---

### Post by grahammechanical on 2013-01-09
> It bothers me that in Ubuntu, a user can change any system settings using just his own user password. I would like to change this before my mother (by accident) deletes her user account.

So, users of Fedora cannot do this?

If that user has administration privileges then it is only natural that the user can change system settings. Who else would do it if not the user whose user name and password were entered as part of the installation process.

With Ubuntu we do not run as root. We only get administration privileges when we need to make serious system changes.

When installing you could have set yourself up as the user. You would have then been the system administrator and with that power you could have created a standard user account for your mother. But it is unreasonable to expect the OS to deny even a standard user the power to change the clock time.

In Ubuntu we cannot change the system language unless we open a utility in System Settings. Was your mother using firefox to do email by web mail from the ISP? Then she may have changed the language setting of Firefox. Is this what happened? Could such a thing not happen in Fedora?

---

### Post by blnl on 2013-01-09
> **grahammechanical said:**
> So, users of Fedora cannot do this?


No, a user in Fedora is not automaticaly added to sudo group. So with ordinary user pasword you can only login and unlock the keyring.

My wife and son both have a user account on our Fedora desktop, and they can´t do anything what is beyond ordinary user prvileges. They can´t install/remove software packages, can even consume updates, nor change the system time and date (without the root pasword that I keep for myself). That is pretty safe, never had an accident like this before.

---

### Post by haqking on 2013-01-09
> **blnl said:**
> No, a user in Fedora is not automaticaly added to sudo group. So with ordinary user pasword you can only login and unlock the keyring.

My wife and son both have a user account on our Fedora desktop, and they can´t do anything what is beyond ordinary user prvileges. They can´t install/remove software packages, can even consume updates, nor change the system time and date (without the root pasword that I keep for myself). That is pretty safe, never had an accident like this before.

remove them from the sudo group.

If you are the admin it is upto you who has admin privelege.

---

### Post by blnl on 2013-01-09
> **grahammechanical said:**
> 
In Ubuntu we cannot change the system language unless we open a utility in System Settings. Was your mother using firefox to do email by web mail from the ISP? Then she may have changed the language setting of Firefox. Is this what happened? Could such a thing not happen in Fedora?

No it was not Firefox. It was an eMail in Thunderbird, normally a default spelling is Dutch, but this time she was writing an eMail in Croatian.
She explained exactly what she did. She opened Dash Home, typed in ¨language¨, and there it is Language Support. From there on, it is just a meter of pressing some buttons. When she was asked for password, she entered her user password.
That is how it´s done.

---

### Post by haqking on 2013-01-09
> **blnl said:**
> No it was not Firefox. It was an eMail in Thunderbird, normally a default spelling is Dutch, but this time she was writing an eMail in Croatian.
She explained exactly what she did. She opened Dash Home, typed in ¨language¨, and there it is Language Support. From there on, it is just a meter of pressing some buttons. When she was asked for password, she entered her user password.
That is how it´s done.

remove her from the sudo group.

---

### Post by blnl on 2013-01-14
Thank you all, I considered your suggestions, but I could not converge to a satisfactory solution. (I do not want to create additional user account for myself on a machine that I will never use. Hence I can't remove her from the sudo group, as that will make impossible to perform any admin tasks.)

Instead, I decided to change the password and make the machine auto-login at startup.
There is still a minor issue. When the machine goes in sleep mode, at wake-up it still asks for the password to unlock the screen.

Is it possible to auto-unlock screen too?
If yes, please explain how to do it.

---

### Post by snowpine on 2013-01-14
You must have at least 1 admin/sudo user on the computer. Everybody's advice so far is right on target: Create a non-sudo user for her everyday tasks, and use the sudo user for admin only.

I'm uncomfortable with your suggestion to obscure the password to her own computer from your mom. Have you thought where that would leave her if something happens to you? (Although, it's actually [trivially easy]("http://www.psychocats.net/ubuntu/resetpassword") to reset the password.)

Just say something like "Mom, here's your password for everyday stuff, and then here's the login info for the admin user in case you ever need it. Next time don't click on stuff you're not sure what it does, call me first!"

---

### Post by blnl on 2013-01-15
> **snowpine said:**
> You must have at least 1 admin/sudo user on the computer. Everybody's advice so far is right on target: Create a non-sudo user for her everyday tasks, and use the sudo user for admin only.

I'm uncomfortable with your suggestion to obscure the password to her own computer from your mom. Have you thought where that would leave her if something happens to you? (Although, it's actually [trivially easy]("http://www.psychocats.net/ubuntu/resetpassword") to reset the password.)

Just say something like "Mom, here's your password for everyday stuff, and then here's the login info for the admin user in case you ever need it. Next time don't click on stuff you're not sure what it does, call me first!"

The advice is perfectly OK, I never questioned the value of the advice I received.
Only, I don't like to create another user account (it's a personal preference), because it will create home directory for that user, and it will also show at the login screen, etc.
Moreover, what name to give to the other account? Probably I would name it Root or Admin. You see the difficulty? I even disabled Guest access. I like to keep it simple and clean.

Don't worry about my mom, she has the other password, but I have made it so difficult that it's practically impossible to know it by hearth. 

If I can only find a way to auto unlock screen after sleep, then I'm done. She will never need to use that password again.

Otherwise, I'll just activate the root account. At least it will not create any directory at users home area. I hope I'll be able to hide it from the login screen too.

---

### Post by sdowney717 on 2013-01-15
I have the same type problems with my 78 yr old father in law. He manages to mess up things a lot as he explores the computer. Then I get to figure out what he did.

I put cinnamon desktop on, and the hot corner caused him a lot of grief.

He would shoot the mouse to the top left and then you get the workplace selector, then he clicked the plus button on right so many times all the added workplaces receded until they become grey goo. He was unable to then use the pc for a full day as he did not know to put the mouse back to the hot corner to show a desktop.

I did find a way to disable the hot corner on a mint forum.

He also deletes a lot of stuff, then claims it was never there.

So even not involving sudo privileges, he messes up how it works.

---

### Post by Time Sheep on 2013-01-15
> **blnl said:**
> The advice is perfectly OK, I never questioned the value of the advice I received.
Only, I don't like to create another user account (it's a personal preference), because it will create home directory for that user, and it will also show at the login screen, etc.
Moreover, what name to give to the other account? Probably I would name it Root or Admin. You see the difficulty? I even disabled Guest access. I like to keep it simple and clean.

Don't worry about my mom, she has the other password, but I have made it so difficult that it's practically impossible to know it by hearth. 

If I can only find a way to auto unlock screen after sleep, then I'm done. She will never need to use that password again.

Otherwise, I'll just activate the root account. At least it will not create any directory at users home area. I hope I'll be able to hide it from the login screen too.

Personally I'd create a user in my own name, then create a standard user for my mother.
At this point you could then set your mothers account to autologin, this is also a far more effective way of starting your computer, as you won't have to enter your password before the keyring is needed.

---

### Post by blnl on 2013-01-18
I found it, it is actually pretty easy to disable screen locking on wake up from sleep mode.
It was there all time in front of me, but I did not see it.

_> System Settings
___> Brightness and Lock
_____> Require my password when waking from suspend

Now I'm done. My mom will never need to use the password again.

I also tarred her home directory and stored it in her Dropbox. Just in case.

---

### Post by Petro Dawg on 2013-01-18
You may also consider installing [TeamViewer7]("http://www.teamviewer.com/en/index.aspx") on her PC (and yours) so you can remotely access her PC and "fix" problems she might encounter.  That's what I've done for my mother who lives 16+ hours away.

---

### Post by blnl on 2013-01-18
> **Petro Dawg said:**
> You may also consider installing [TeamViewer7]("http://www.teamviewer.com/en/index.aspx") on her PC (and yours) so you can remotely access her PC and "fix" problems she might encounter.  That's what I've done for my mother who lives 16+ hours away.

Yes, I already installed x11vnc server and configured it to start at boot.

---

