---
title: "[SOLVED] broken Java install"
date: 2008-04-27
forum: General Help
---

### Post by Rytron on 2008-04-27
Hi,
I came across a website that needed  Java.
I tried to install it in Firefox but this would not work.
So I went to add/remove and found Sun Java 6 Runtime.

I started to install it. It took ages. Then it stopped responding.

Now I have a broken install.

When I go to synaptic packet manager I get this message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

What must I do?

---

### Post by ibuclaw on 2008-04-27
Naturally, you would open a terminal and type in:
```
sudo dpkg --configure -a
```

If you want Java for Firefox.
```
sudo apt-get install sun-java6-plugin ubuntu-restricted-extras
```

Regards
Iain

---

### Post by Rytron on 2008-04-27
I went to the terminal and typed:

```
su

```

to enter as superuser (sudo would not suffice)

then I typed in:

```
dpkg --configure -a
```

Now though I am left with two broken packages.

:confused:

---

### Post by ibuclaw on 2008-04-27
What are the two packages that are broken?

Copy and paste the output of the error message in your next post.

Thanks

Regards
Iain

---

### Post by fragos on 2008-04-28
Debian releases like Ubuntu don't use su. Run "sudo dpkg --configure -a" and use your own password when prompted.

---

### Post by Mr Frosti on 2008-04-28
Well, the good news is that Sun is in talks with Ubuntu about shipping Java out of the box in several Linux distributions once Java goes 100% GPL. This means it will "just work".

What packages are  being reported as broken? Using "Synaptic Package Manager", you can also try "Edit -> Fix Broken Packages". This essentially does the same thing as running "dpkg --configure -a"

---

### Post by Rytron on 2008-04-28
When I go to synaptic packet manager I go to edit>fix broken packages.
Then I click apply.
It says:

To be upgraded
sun-java6-bin
sun-java6-jre

I know that when I try to upgrade it will eventually crash again.
I don't want Java.

I tried:

```

sudo dpkg --configure -a
```

the broken packages are still there.

I tried this to get Java for Firefox - no luck. Perhaps it is because of the broken packages problem.

```
sudo apt-get install sun-java6-plugin ubuntu-restricted-extras
```

:confused:

---

### Post by Bablefish on 2008-04-28
Have you check out add remove? Java is in there.

---

### Post by forrestcupp on 2008-04-28
You could try
```
sudo apt-get -f install
```
To automatically fix the broken dependencies.  Then try the command you posted to try to install again.
```
sudo apt-get install ubuntu-restricted-extras
```
The restricted-extras package includes the Java plugin.

---

### Post by Rytron on 2008-04-28
Hi,
I want to get rid of Java.
It wont install properly. I tried twice to install it.

:shock:

---

### Post by forrestcupp on 2008-04-28
I think you probably need to get it installed properly with the command I gave you before you can uninstall it.  It probably failed the first time because you didn't realize you had to agree to their license before it will finish installing.

---

### Post by Rytron on 2008-04-29
Hi forrestcupp,
Thank you for persevering with this thread.

Okay, I have started with your advice again.

I used

```
sudo apt-get -f install
```

Now I have the screen (attached).
How do I choose OK?

---

### Post by mali2297 on 2008-04-29
> **Rytron said:**
> H
Now I have the screen (attached).
How do I choose OK?

Press TAB so that OK gets highlighted. Then press ENTER.

---

### Post by Rytron on 2008-04-29
Thanks everyone. Java is now sorted and installed. No broken packages.
I wish the 'mark this thread as solved' feature returned as this thread is now solved.

:popcorn:

---

