---
title: "Memory Bug?"
date: 2022-06-04
forum: General Help
---

### Post by jacksonguitars on 2022-06-04
Dear sirs and ladies!

I get this weird message in Ubuntu. I have 8gb ram installed. But only 4gb of ram show up in "About Ubuntu".

However 8 gb of ram show up in the terminal. So whats the deal here? Is my computer using 4 or 8gb of ram?

Thank you.

Best regards
Richard

---

### Post by mIk3_08 on 2022-06-04
> **jacksonguitars said:**
> Dear sirs and ladies!
I get this weird message in Ubuntu. I have 8gb ram installed. But only 4gb of ram show up in "About Ubuntu".
However 8 gb of ram show up in the terminal. So whats the deal here? Is my computer using 4 or 8gb of ram?
Thank you.

Best regards
Richard
Very strange thing. Yeah. this is possible. I haven't encounter this thing but I have encounter a lot of bugs in my Linux Ubuntu Operating System too. But glad to say that I solve the issue then. That was long time ago. But this thing maybe involves in the initialization thing. Regards and Cheers.

---

### Post by Impavidus on 2022-06-04
Your screenshot is a bit hard to read, but I can manage. We usually ask our users to post terminal output as text, not screenshots. And for the other window, cropping it to just that window works better than showing the entire screen.

Anyway, free without any arguments is supposed to output in kibibytes, so that means 7.7GiB memory according to free. This in contrast to tools reporting hard drive size, which are usually half kibibytes. To be really sure about the units, give them explicitly. For example```
free -h
```
When command line tools and GUI tools disagree, we tend to believe the command line tools. You can also look it up in UEFI/bios.

Sometimes part of your ram is reserved for graphics. It depends on your graphics hardware. Then free will report less memory than is installed, as it doesn't report video ram.

My guess is you have 8.0GiB memory installed, 7.7GiB usable and 0.3GiB reserved for whatever, and the GUI tool is wrong.

---

### Post by deadflowr on 2022-06-04
I'd look at what it shows in System Monitor (in the Resources tab).
I would guess the output from About Ubuntu is wrong.

I found the same issue reported for (or about) arch here: [https://gitlab.gnome.org/GNOME/gnome-control-center/-/issues/1686]("https://gitlab.gnome.org/GNOME/gnome-control-center/-/issues/1686")
Not that it helps in this case since that's a completely different operating system.

---

### Post by #&amp;thj^% on 2022-06-04
> **jacksonguitars said:**
> Dear sirs and ladies!

I get this weird message in Ubuntu. I have 8gb ram installed. But only 4gb of ram show up in "About Ubuntu".

However 8 gb of ram show up in the terminal. So whats the deal here? Is my computer using 4 or 8gb of ram?

Thank you.

Best regards
Richard

I always rely on the terminal, no GUI stuff...
```
grep MemTotal /proc/meminfo
MemTotal:        7486364 kB

```
or:
```
inxi -m
Memory:
  RAM: total: 7.14 GiB used: 5.24 GiB (73.4%)
  RAM Report:
    permissions: Unable to run dmidecode. Root privileges required.

```
Just a couple of other methods to check first.
```
free
               total        used        free      shared  buff/cache   available
Mem:         7486364     5129272      740980       46432     1616112     2011120
Swap:         524284      503872       20412


```
```
vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 0  0 503872 747856  21884 1593372    0    0    75     9  342  257  2  2 96  0  0



```
Top && Htop will also work

---

### Post by mIk3_08 on 2022-06-05
Can anyone here explain how could this happen? This is a bet strange and weird. And why this is happening? 
This image is same as the upload image above. Regards and cheers. 
 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=290574&stc=1[/IMG]

---

### Post by jacksonguitars on 2022-06-07
Thank you, sir. I would also trust the terminal over the gui in a situation like this.

My BIOS also returns 8gb of RAM.

---

### Post by mIk3_08 on 2022-06-07
> **jacksonguitars said:**
> Thank you, sir. I would also trust the terminal over the gui in a situation like this.
My BIOS also returns 8gb of RAM.
I don't know how can I explain this kind of issue but surely this is possible. It can happen during the initialization maybe. How about the performance of your Linux Ubuntu Operating System. Any issue? I don't get surprise anymore about this situation as I am already immune to this issues of Linux Ubuntu Operating System. Though not same thing as this but some issues that are manageable. Regards and Cheers.

---

### Post by #&amp;thj^% on 2022-06-07
If it really bothers you, file a bug against "gnome-control-center"
On my KVM it reads correctly, I've allowed 4 Gigs of ram for that setup.
One person has reported the issue here: [https://github.com/pop-os/gnome-control-center/issues/228](https://github.com/pop-os/gnome-control-center/issues/228)
```
free
               total        used        free      shared  buff/cache   available
Mem:         4019056     1590320     1164864       92216     1263872     2092124
Swap:        1190288           0     1190288

```

---

### Post by mIk3_08 on 2022-06-08
> **1fallen said:**
> If it really bothers you, file a bug against "gnome-control-center"
On my KVM it reads correctly, I've allowed 4 Gigs of ram for that setup.
One person has reported the issue here: [https://github.com/pop-os/gnome-control-center/issues/228](https://github.com/pop-os/gnome-control-center/issues/228)
```
free
               total        used        free      shared  buff/cache   available
Mem:         4019056     1590320     1164864       92216     1263872     2092124
Swap:        1190288           0     1190288

```
This is the best idea. I strongly agree with 1fallen that you should file a bug against "gnome-control-center" [COLOR=#000000]jacksonguitars. So far that is the best thing you can do right now. And surely you can help others too to the new Linux Ubuntu users that can also encounter same bugs as yours. Regards and cheers.[/COLOR]

---

