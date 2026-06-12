---
title: "can't even login after usermod"
date: 2008-02-27
forum: General Help
---

### Post by chocolatetoothpaste on 2008-02-27
Ok, I should know better than this.  I was logged in as, we'll call it "user".  I typed "sudo usermod -d /home/user -p newpass -l newuser user".  I was just trying to change my username.  I booted to recovery mode, I did a few userdel commands, a few passwd commands, I even tried adding totally new users, and I can't log into any of them.  The one account I CAN log in to is the one that was already existing.  Can anyone offer some ideas?

---

### Post by bodhi.zazen on 2008-02-27
Can you give us the error message you receive when you log in ?

Did you set the ownership and permissions on the old $HOME to the new user ?

---

### Post by chocolatetoothpaste on 2008-02-27
Well, I can't get to the error messages.  I ran the command, logged out, and when I tried to login using the new username/password, it acted like the user didn't exist.  Just game me invalid login message.  It's the same with all the new users I created.  I'll boot into recovery mode and see if I can find any relevant messages and post back...

---

### Post by chocolatetoothpaste on 2008-02-27
Well, there were no error messages in /var/log/messages.  I don't think it's the right place to look anyway.  Plus, it doesn't explain why a new user wouldn't be able to log in.  I'm guessing there is a defunct line in a file somewhere, I just don't know where to look.

---

### Post by bodhi.zazen on 2008-02-27
From recovery mode, su to the new user

su user

boot from hard drive -> go to Ctrl-Alt-F1 -> log in as the new user

post any error messages.

Just a guess, but I bet you have a permissions or ownership problems

sudo chown -R new_user.new_user /home/new_user

---

### Post by chocolatetoothpaste on 2008-02-27
Well, for whatever reason, by using adduser I was able to create the user.  Not sure why useradd wasn't working.  At least I got what I needed.  Hopefully whatever broke will fix at some point through updates or whatever.  Thanks for the suggestions though

---

