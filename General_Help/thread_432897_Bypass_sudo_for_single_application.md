---
title: "Bypass sudo for single application?"
date: 2007-05-04
forum: General Help
---

### Post by tylersticka on 2007-05-04
Greetings,

I recently upgraded to Feisty Fawn and I am beyond impressed. Absolutely stellar release, I love seeing the evolution of this OS.

One annoyance I've had has to do with wifi-radar. It's working fine, which is why this isn't in the "Wireless" support category. My problem is that I have to enter a password each time it launches (including at startup), which I think is unnecessary.

I see the value of maintaining sudo prompts, but I can't see the danger in allowing this specific program to launch without password verification. I understand that some wireless networks may be insecure, but it requests a password even on boot when it's starting in the background, and it already has the security measure of not automatically connecting to any network I haven't verified previously.

I searched and was able to find methods of bypassing sudo for all applications for all users, but I'd like to maintain that functionality for everything EXCEPT wifi-radar.

My question is, how can I configure my laptop to bypass the sudo password request for a single program?

Thanks for any help you can give in advance.

---

### Post by 5-HT on 2007-05-04
You can edit /etc/sudoers to allow wifi-radar to not require a password for authentication.

```
 sudo visudo
```At the end of the file add an entry with the following syntax: ```

<username> <host> = (root) NOPASSWD: <path to wifi-radar executable>
```You can find the path to the wifi-radar executable doing the following: ```
which wifi-radar
```eg., username=me hostname=computer executable=/foo/bar

```

me computer = (root) NOPASSWD: /foo/bar 
```To save the sudoers file and exit: Ctrl + x

---

### Post by tgm4883 on 2007-05-04
im not sure about wifiradar (i use networkmanager) but is it really a sudo password request and not a keyring?

I use libpam-keyring because without it i had to enter my keyring password every time i booted up

---

### Post by Hairy_Palms on 2007-05-04
to do it for a single command you can also use
> echo "your password here" | sudo -S "insert command here"

---

### Post by tylersticka on 2007-05-10
I made the edit to etc/sudoers, but it stopped wifi-radar from launching at all, so I took the line out and it started working again. I double-checked to insure my command was correct, and it was, so I'm not sure what the deal was with that.

I tried Hairy Palms' solution, and it worked fine for the autostart. Thanks very much!

---

### Post by tylersticka on 2007-06-13
I thought I'd mention that all my wireless networking problems were solved by ditching wifi-radar in favor of wicd, which I talk about on [this thread]("http://ubuntuforums.org/showthread.php?t=357749&page=2#post2838731").

---

