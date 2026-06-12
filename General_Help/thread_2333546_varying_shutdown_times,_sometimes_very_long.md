---
title: "varying shutdown times, sometimes very long"
date: 2016-08-11
forum: General Help
---

### Post by Skaperen on 2016-08-11
running a fresh install of 16.04 LTS upgraded very regularly, is see varying shutdown times ranging from about 5 seconds to 4 minutes.  on the long ones it is at the 5 dots that keep cycling on color (orange and white). any idea what might be slowing it down?  something over the network something is waiting for?

---

### Post by vasa1 on 2016-08-11
I see this as well although mine is an upgrade from 14.04 to 16.04. It's a bit irritating. Do you use Firefox? If so, *after* you quit Firefox, wait a full minute before shutting down. Does that help?

OS = Lubuntu

---

### Post by Skaperen on 2016-08-11
i don't quit firefox ... yet often the system shutdown is quick, even with several instances of firefox still running under multiple users.  could firefox be varying things when not running?  *waiting a full minute* would be a problem with my goal of a _consistent quick shutdown_.

---

### Post by &amp;KyT$0P# on 2016-08-11
Do you see anything informative during one of these bad shutdowns if you remove the quiet and splash boot parameters?

open /etc/default/grub in a text editor (as root)
remove quiet and splash from the GRUB_CMDLINE_LINUX_DEFAULT line
run [FONT=Courier New]sudo update-grub[/FONT]
reboot

---

### Post by Skaperen on 2016-08-12
> **halogen2 said:**
> Do you see anything informative during one of these bad shutdowns if you remove the quiet and splash boot parameters?

open /etc/default/grub in a text editor (as root)
remove quiet and splash from the GRUB_CMDLINE_LINUX_DEFAULT line
run [FONT=Courier New]sudo update-grub[/FONT]
reboot
i just set that up to see what i get.

i did a 2nd reboot to see how it goes, once.

BTW, i edited the file (as root) with:

```
sed -i 's/quiet and splash//' /etc/default/grub
```

i should have done:

```
sed -i~ 's/quiet and splash//' /etc/default/grub
```

---

### Post by decrepit on 2016-08-12
This is also happening to me on a fresh install of mate 16.04 I assumed it was a filesystem check every so often. I haven't kept a note of how often it happens, or how regular it is.

---

### Post by &amp;KyT$0P# on 2016-08-12
> **Skaperen said:**
> BTW, i edited the file (as root) with:

```
sed -i 's/quiet and splash//' /etc/default/grub
```

i should have done:

```
sed -i~ 's/quiet and splash//' /etc/default/grub
```
Sorry, I meant "quiet" and "splash" separately, not the whole phrase "quiet and splash".

---

### Post by vasa1 on 2016-08-12
Is this really [SOLVED]?

---

### Post by Skaperen on 2016-08-12
> **halogen2 said:**
> Sorry, I meant "quiet" and "splash" separately, not the whole phrase "quiet and splash".

it was "quiet splash".  this means a correction of my command posting which was manually typed in because i actually used my sedi script which does it for me, with the ~ option to save the old file.

```
#!/bin/bash
s="${1}"
c='~'
shift
for n in "$@"; do
    ls -l "${n}" || exit 1
done
for n in "$@"; do
    sed "-i${c}" "${s}" "${n}"
done
for n in "$@"; do
    ls -l "${n}"
    ls -l "${n}${c}"
done
```

---

### Post by Skaperen on 2016-08-12
in the sense of will there be more posts here about this ... probably not.  but how to find individual issues like this, i'd say an answer is here.

---

### Post by pqwoerituytrueiwoq on 2016-08-13
if you press the up or down arrow key during boot or shutdown (during the splash screen) it will show you what it happening
i use xubuntu and also have this issue

---

### Post by decrepit on 2016-08-17
So, have you found what is causing the long delays? 
Since I removed quiet and splash, it hasn't done a long one.

---

### Post by banceu_sergiu_ione on 2016-08-17
If the slow shutdown happen often you can check for unkillable processes. To do this you have to uncomment the ' report_unkillable ' in /etc/init.d/sendsigs and enable apport ( enabled=1 in etc/default/apport ) then shutdown. Apport will show you a crash report when log in or you can check the var/crash for logs. 
[Here you can see more about apport and why it is disabled by default]("https://wiki.ubuntu.com/Apport"), better don't start send reports for all crashes it show if you run a stable OS release.

Also have a look at syslog/kern.log/boot.log , just check all you have and see if can find any information of same error/crash at the shutdown time.

---

### Post by Skaperen on 2016-09-16
yesterday, i had one of those long shutdowns.  it lasted about 2 minutes.  i had enabled the message output as described above and it has been working but yesterday they did not show at all. nothing showed. i had about 2 minutes of a black screen before the system powered off.

any ideas?

---

