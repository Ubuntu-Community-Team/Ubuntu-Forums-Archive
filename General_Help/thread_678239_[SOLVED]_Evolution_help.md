---
title: "[SOLVED] Evolution help"
date: 2008-01-25
forum: General Help
---

### Post by WildeBeest on 2008-01-25
Is there a way to set Server port settings to a specific port number?

---

### Post by plucky on 2008-01-25
WildeBeest


```
pop.your.server.name:your_port_number
``` and ```
smtp.your.server.name:your_port_number
```

Good luck

---

### Post by WildeBeest on 2008-01-25
I'm a total noob.

I'm setting up multiple e-mail accounts in evolution.
Most of them are not the default imap port 143 and smtp 25  numbers.

Please give me detailed instructions.

---

### Post by dcstar on 2008-01-25
> **WildeBeest said:**
> I'm a total noob.

I'm setting up multiple e-mail accounts in evolution.
Most of them are not the default imap port 143 and smtp 25  numbers.

Please give me detailed instructions.

The previous poster just did, again:

imap.server.name:143 (or whatever)

smtp.server.name:25 (or whatever)

It cannot be made any simpler.

---

### Post by WildeBeest on 2008-01-26
Simple sure. But, where are those commands executed?

---

### Post by spec-chum on 2008-01-26
They're not commands that you execute.  That how you specify the server details in the Receiving E-Mail and Sending E-Mail tabs in Evolution's preferences
if you need to use different port numbers than the defaults.

---

### Post by WildeBeest on 2008-01-26
I got it, you just append the port number to the end ':993'.

I was looking for an edit box like in Thunderbird.

Thanks to all.

Now if I can get a solution to my 'dpkg' problem.

---

