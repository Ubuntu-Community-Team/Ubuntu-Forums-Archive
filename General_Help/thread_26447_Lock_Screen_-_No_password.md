---
title: "Lock Screen - No password"
date: 2005-04-13
forum: General Help
---

### Post by stwog on 2005-04-13
Hello,

I tried out Ubuntu live on a laptop with a dead hard drive. I think it works really well. I never thought linux on a laptop would be so easy and work so well.

I have found one important problem though. When I close the laptop, the computer goes into some state of hibernation and when I open it up again the screen is locked and requires a password to get rid of the screen saver. Unfortunately there is no password for the 'ubuntu' user, so there is no way to unlock the screen. BTW, simply pressing enter at the password prompt does not work.

Anyone know a way to fix this?

Simon

---

### Post by Tiede on 2005-04-19
This seems a little bit odd...
Try typing ubuntu or guest...
But I think it would be better to do 'sudo passwd ubuntu' in a terminal and set one yourself...

---

### Post by ogomoe on 2005-04-30
It's too late to use the terminal.

I'm also looking through the forum for the same answer.

What is the password for the `ubuntu` user on the live CD?

---

### Post by aulin on 2005-05-02
Hi

I am not sure what the password is but a way around the issue is to do ctrl-alt-f1 then at the prompt type:

sudo passwd ubuntu

and make the password what ever you want.  Then go back to the X screen with ctrl-alt-f7 and log back in

Hope that helps

---

### Post by SChipS on 2005-05-11
Yep, I see this as no small problem.

Ubuntu encourages users to distribute the distribution freely as we wish. I had a friend accidently lock the screen and that was enough for him. He let his computer in that DENIED state for 3 hours until I could see it and re-boot the system for him.

Since it is a Live CD, the "ubuntu user" password should be published freely, it must be the same for every live CD, I would certainly think.

That would keep new folks out of trouble anyway.

SChipS

---

### Post by millerlite86 on 2005-06-06
This is a modified reply that I gave to another post ([http://ubuntuforums.org/showthread.php?t=34570)](http://ubuntuforums.org/showthread.php?t=34570)).

I am not sure what the password is for the default "ubuntu" username, but a way around this is to (before you close your laptop, preferably immediately after startup):

1. From the Menu "System" --> "Administration" --> "Users and Groups"
2. Click on user "ubuntu"
3. Select "Properties"
4. Under the "Password Section" "Set Password by Hand" should be checked
5. Delete the *'s in box 1 and enter a password, eg. hello
6, Delete the *'s in box 2 and rekey the same password as in box 1
7. Click "Ok"

Your Live CD will now have this new password saved for the "ubuntu" login for this Live CD session. (When you boot Live CD again later this change will not be saved.)

Hope that helps!

---

### Post by Tiede on 2005-08-10
I know this might be a little late, but you can also take out that option by going in System->Preferences->Screen Saver and clearing the second box that says lock screen after X mns.
But I fear you will have to do this everytime you open the Computer though, since the settings on a LivecD are not loaded at the next session.

---

