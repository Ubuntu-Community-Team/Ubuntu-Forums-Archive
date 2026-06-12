---
title: "[SOLVED] Wrong user name or password"
date: 2007-09-02
forum: General Help
---

### Post by Vince329 on 2007-09-02
I just installed ubuntu 7.0 after much trouble with trying to partition. Didn't know what I was really doing.
I have an older Dell laptop w/20G HD and 512 mem. The install would always fail because I couldn't partition. I quit, restarted the comp but I couldn't boot into windows. I did change the boot sequence back to HD. Windows won't start. It says to press any key but nothing happens. I can't reinstall windows from the installation disk either. 

I could boot into ubuntu so I don't care about windows. When I get to the user name and password it rejecks it saying it is wrong. At setup I put in a user name and password that I always use on my comp. I know it is case sensitive. How can I get by this? Will I need a new HD and start over? So right now I can't use an OS.

Please help

---

### Post by aysiu on 2007-09-02
It is possible that you mistyped the password the first time. If that's the case, you can reset the password.

**Step 1**:
Reboot

**Step 2**:
Select *Recovery Mode*

**Step 3**:
At the command prompt, type ```
cd /home
ls
``` Verify the correct spelling of your username. Let's assume, for this example, that it's *vince*.

**Step 4**:
Reset your password by typing this command: ```
passwd vince
```

**Step 5**:
Reboot ```
reboot
``` and select normal boot mode.

---

### Post by PmDematagoda on 2007-09-02
This thread could be useful for you:-

[http://ubuntuforums.org/showthread.php?t=529583&highlight=Recovering+your+password](http://ubuntuforums.org/showthread.php?t=529583&highlight=Recovering+your+password)

---

### Post by PmDematagoda on 2007-09-02
I was pointing to the same thing but your's is easier Aysiu.:)

---

### Post by Vince329 on 2007-09-02
I press F2 to enter setup. Is that what you refer to as recovery mode?

---

### Post by aysiu on 2007-09-02
> **Vince329 said:**
> I press F2 to enter setup. Is that what you refer to as recovery mode?
No, it's after that screen. F2 is to enter your BIOS setup. The Grub menu appears *after* that.

When you boot up...

**If you're dual-booting**
Press the Down arrow when you're at the Grub menu

**If you're single-booting**
Press Escape and then the Down arrow

See the attached screenshot for more details.

---

### Post by Vince329 on 2007-09-02
Don't know if I did this right but I get to a prompt that says Enter new unix password. I can't type anything.The prompt keeps blinking.

---

### Post by aysiu on 2007-09-02
> **Vince329 said:**
> Don't know if I did this right but I get to a prompt that says Enter new unix password. I can't type anything.The prompt keeps blinking.
Your password is being accepted. You just aren't getting any visual feedback. It's not "for security reasons," as some people will try to tell you. It's a bug that will never be fixed. More details here: [http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

Just keep typing and hit *Enter* when you're done.

---

### Post by Vince329 on 2007-09-02
I must really be thick. You say keep typing. Where it says Enter new unix password I can't type anything there. I go through the motions of typing a new password and hit enter. Then it says Retype new unix password. Again I go through the motion of typing, the prompt doesn't move. I hit enter, and get Sorry passwords do not match.

---

### Post by aysiu on 2007-09-02
No, you're not thick. This is just a cultural adjustment.

When it says *Enter new unix password*, go ahead and type and hit *Enter* when you're done. Type **slowly** so that you are sure you're being consistent.

Once you hit *Enter*, it will ask you to *Retype new unix password*, do the same (just type and hit *Enter* when done).

It's looking for you to type the exact same password twice. Do not hit *Backspace* if you mess up. The two passwords have to be **exactly** the same. Type **slowly** to make sure they match.

---

### Post by Vince329 on 2007-09-02
I don't believe it but after 3 more tries it took it. Rebooted and at my new empty desk top. Thanks so much for staying with me.

---

