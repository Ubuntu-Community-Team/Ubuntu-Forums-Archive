---
title: "Is this installation 64 bit?"
date: 2008-04-27
forum: General Help
---

### Post by jimmy the saint on 2008-04-27
How does one tell if they are running a 64 but installation?

Thanks

---

### Post by LaRoza on 2008-04-27
What is your processor?

If you don't know, post the output of:

```

cat /proc/cpuinfo

```

Do this instead:

```

uname -a

```

---

### Post by jimmy the saint on 2008-04-27
I know my processor is 64 bit (core 2 duo).  I got the laptop from a buddy last night and I have no idea what iso he used to intall hardy.  I can't find information anywhere that indicates whether or not this installation is 64 bit or not.

---

### Post by LaRoza on 2008-04-27
> **jimmy the saint said:**
> I know my processor is 64 bit (core 2 duo).  I got the laptop from a buddy last night and I have no idea what iso he used to intall hardy.  I can't find information anywhere that indicates whether or not this installation is 64 bit or not.

Run the second command (sorry, I had edited by post)

---

### Post by jimmy the saint on 2008-04-27
Linux ThinkUbuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux


is that 64 bit?

---

### Post by LaRoza on 2008-04-27
> **jimmy the saint said:**
> <code>Linux ThinkUbuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
</code>

is that 64 bit?

Nope, it is 32 bit. i686 is 32 bit.

---

### Post by pbpersson on 2008-04-27
Here is how 64-bit would appear:

Linux phil-desktop-Linux-test 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

---

### Post by jimmy the saint on 2008-04-27
Ah.  Hey thanks man.  
Out of curiosity, what would it say if it was 64 bit?  Oh yeah, and how did you get those code tags to work?  I editied that post like 8 times playing with them and you saw the result!!

Anyways thanks for the help!

---

### Post by LaRoza on 2008-04-27
> **jimmy the saint said:**
> Ah.  Hey thanks man.  
Out of curiosity, what would it say if it was 64 bit?  Oh yeah, and how did you get those code tags to work?  I editied that post like 8 times playing with them and you saw the result!!

Anyways thanks for the help!

x86_64 instead of i686 I think.

[noparse]```
I just type them in to get code.
```[/noparse]

---

### Post by jimmy the saint on 2008-04-27
That makes sense.  Thanks guys.

---

### Post by dcstar on 2008-04-27
> **LaRoza said:**
> 
........
[noparse]```
I just type them in to get code.
```[/noparse]

Code tags are inserted by highlighting the text and selecting the "#" (Code) icon in the formatting task bar above your message.

---

### Post by LaRoza on 2008-04-27
> **dcstar said:**
> Code tags are inserted by highlighting the text and selecting the "#" (Code) icon in the formatting task bar above your message.

I use the plain text editor with no buttons ;)

---

### Post by dcstar on 2008-04-27
> **LaRoza said:**
> I use the plain text editor with no buttons ;)

Then tell the other person who asked the question this important information when you supply an answer that may well cause that person to use a method that is not appropriate for them.

---

### Post by LaRoza on 2008-04-27
> **jimmy the saint said:**
> Ah.  Hey thanks man.  
Out of curiosity, what would it say if it was 64 bit?  Oh yeah, and **how did you** get those code tags to work?  I editied that post like 8 times playing with them and you saw the result!!


> **dcstar said:**
> Then tell the other person who asked the question this important information when you supply an answer that may well cause that person to use a method that is not appropriate for them.

Why? I have only used this plain text box, and don't know what the GUI version look like or what it can do.

Also, I answered the question (which is bolded). The method is appropriate for them.

---

