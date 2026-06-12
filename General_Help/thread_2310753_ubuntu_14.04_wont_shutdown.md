---
title: "ubuntu 14.04 wont shutdown"
date: 2016-01-21
forum: General Help
---

### Post by farbod3 on 2016-01-21
hi,

I know its a common problem but as far as I've searched i found no solution for this !

No command works neither "shutdown" nor "reboot"

anyone any idea?

---

### Post by maxinstuff2 on 2016-01-21
Does reboot work using sudo?

```
sudo reboot
```

And does shutdown/reboot work through Unity/other DE?

---

### Post by pqwoerituytrueiwoq on 2016-01-21
i use [FONT=courier new]sudo poweroff[/FONT] instead of [FONT=courier new]sudo halt[/FONT] as i have had halt not turn off some system

---

### Post by Edward_Fish on 2016-01-22
Ok, I'll need a little more detail.
Run "sudo poweroff" or "sudo shutdown -hP now"
What should happen is applications close, the screen fills with purple, the word ubuntu is displayed in the middle of the screen above some dots which change colour. Once you reach that screen, press ESC on the keyboard. You should see a the screen change to a command line thingy showing the shutdown process.
Tell me what appears in the command line thingy. Specifically, the last 2-3 lines.

---

### Post by farbod3 on 2016-01-22
> **maxinstuff2 said:**
> Does reboot work using sudo?

```
sudo reboot
```

And does shutdown/reboot work through Unity/other DE?

no actually, when i use it it just freeze !
and i use unity !

> **Edward_Fish said:**
> Ok, I'll need a little more detail.
Run "sudo poweroff" or "sudo shutdown -hP now"
What should happen is applications close, the screen fills with purple, the word ubuntu is displayed in the middle of the screen above some dots which change colour. Once you reach that screen, press ESC on the keyboard. You should see a the screen change to a command line thingy showing the shutdown process.
Tell me what appears in the command line thingy. Specifically, the last 2-3 lines.

i tried "shutdown -h now" , the taskbar on top and the dock (or whatever it called) disappear but the the applications remain on page and nothing will happen next and everything freezes ! the only thing i can do next is hold the power key to shutdown the system !

(sorry for bad english btw!)

none of these worked guys no other idea ?:/

---

### Post by Nuno_Abreu on 2016-01-23
I normally use this command to reboot:
```
sudo shutdown -r 0
```

And if I remember it correctly, this is way I poweroff the system (the only way that worked for me):
```
sudo shutdown -H 0
```

---

### Post by Petro Dawg on 2016-01-23
I tend to go a bit overboard when faced with this kinds of issues.  Typically I will throw the baby out with the bath water and just install a different OS and see if that resolves the issue.  For example, I had the same issue when testing the latest Fedora release, which worked great except I could not get the thing to shut down properly; installed Ubuntu and problem solved.  

Seems to me some distros just work better with some hardware than others.  Would you be willing to try Mint or Fedora or something else?   I've gotten to the point where installing a new OS is faster than troubleshooting (and I personally enjoy trying other Linux distros from time to time as well), that may not able a good solution for you, but that is just me and my 2 cents.

---

### Post by farbod3 on 2016-01-24
> **Nuno_Abreu said:**
> I normally use this command to reboot:
```
sudo shutdown -r 0
```

And if I remember it correctly, this is way I poweroff the system (the only way that worked for me):
```
sudo shutdown -H 0
```

no .... not working

> **Petro Dawg said:**
> I tend to go a bit overboard when faced with this kinds of issues.  Typically I will throw the baby out with the bath water and just install a different OS and see if that resolves the issue.  For example, I had the same issue when testing the latest Fedora release, which worked great except I could not get the thing to shut down properly; installed Ubuntu and problem solved.  

Seems to me some distros just work better with some hardware than others.  Would you be willing to try Mint or Fedora or something else?   I've gotten to the point where installing a new OS is faster than troubleshooting (and I personally enjoy trying other Linux distros from time to time as well), that may not able a good solution for you, but that is just me and my 2 cents.

well thats a little hard for me ... my applications my files :/ how you manage that?

---

### Post by Nuno_Abreu on 2016-01-25
> **farbod3 said:**
> no .... not working
Did you run the command as root? If you did, I'm not sure... It just seems to me you did a bad update and it broke your system. Try a Live-CD and try the mentioned commands in the Terminal and check if you have the same results. If you can't, you could be facing an hardware issue, which is unfortunate.

---

### Post by Vladlenin5000 on 2016-01-25
> **farbod3 said:**
> no .... not working

Did you notice any error messages? Please post the entire error. If no obvious error, where exactly did it stop/hanged the shutdown/reboot process?

---

