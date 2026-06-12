---
title: "[SOLVED] Need HELP!!! BAD =("
date: 2008-07-02
forum: General Help
---

### Post by ukferrari on 2008-07-02
Hi there, I am very new to Ubuntu I have 8.04 LTS. When I go to open the "Synaptic Package Manager" nothing happens? Please help as I really want to use Ubuntu as my standard O.S. not Windows.

Many Thanks
Ukferrari

---

### Post by Separ on 2008-07-02
What happens if you try to open it in terminal?

```
sudo synaptic
```

---

### Post by VMC on 2008-07-02
> **ukferrari said:**
> Hi there, I am very new to Ubuntu I have 8.04 LTS. When I go to open the "Synaptic Package Manager" nothing happens? Please help as I really want to use Ubuntu as my standard O.S. not Windows.

Many Thanks
Ukferrari

What do you mean nothing happens? Did it ask for your password before you entered. Is the display not working. 

Nothing happens. You mean absolutely nothing?

---

### Post by ukferrari on 2008-07-02
it pops up "Starting without Administrative Privileges"

---

### Post by ukferrari on 2008-07-02
> **VMC said:**
> What do you mean nothing happens? Did it ask for your password before you entered. Is the display not working. 

Nothing happens. You mean absolutely nothing?

Well when I click the logo to open it nothing opens, there are no pop-ups or anything just nothing.

---

### Post by ukferrari on 2008-07-02
Bump

---

### Post by Separ on 2008-07-02
Did you just type "synaptic" in the terminal and not "sudo synaptic"?

---

### Post by ukferrari on 2008-07-02
> **Separ said:**
> Did you just type "synaptic" in the terminal and not "sudo synaptic"?

yea

---

### Post by ukferrari on 2008-07-02
if I type "sudo synaptic" it says "sudo: unable to resolve host oliver-laptop"

---

### Post by Separ on 2008-07-02
EDIT: Just read above post.

Can you post the output of:

```
cat /etc/hosts
```

---

### Post by ukferrari on 2008-07-02
oliver@oliver-laptop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 oliver-laptop.home

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.1 linksys

---

### Post by Separ on 2008-07-02
type this in a terminal:

```
gksudo gedit /etc/hosts
```

and make it look like this:

```
127.0.0.1 localhost
**127.0.1.1 oliver-laptop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.1 linksys
```

Lines to change are shown in bold. Save the file after you are done.

---

### Post by ukferrari on 2008-07-02
it will not let me save the edited text it says:

 "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

---

### Post by Separ on 2008-07-02
did you do gksudo before it or just type gedit /etc/hosts?

---

### Post by ukferrari on 2008-07-02
> **Separ said:**
> did you do gksudo?

When I type that nothing happens no windows open or anything. it only comes up if I leave out the "gksudo"

---

### Post by Separ on 2008-07-02
On the off chance that this works: try

```
gksu gedit /etc/hosts
```

---

### Post by ukferrari on 2008-07-02
nope same as before, nothing at all happens

---

### Post by Separ on 2008-07-02
I thought as much.

Write this all down on a bit of paper or something because I'm going to ask you to boot into recovery mode which has no grapical interface, just a terminal:

Reboot your computer into recovery mode by selecting the recovery mode option from the grub menu.

When it boots into a terminal, you automatically have root permissions.

Type
```
sudo nano /etc/hosts
```
And edit the line as before. Hit Ctrl+X to exit and when it asks you if you want to save it, hit "y"

Then type
```
sudo reboot
```
And boot as normal.

---

### Post by ukferrari on 2008-07-02
ok I have done all that and nothing went wrong

---

### Post by Separ on 2008-07-02
Good good, try opening synaptic again.

---

### Post by ukferrari on 2008-07-02
It WORKS!!! 

Thank you so much, your support and patience has been most appreciated.

Thanks Again

Ukferrari (Oliver)

---

### Post by Separ on 2008-07-02
Hehe, no problem.

Don't forget to thank useful posts :D ;)

Also mark this as [SOLVED] using the "Thread Tools" at the top of the page.

---

