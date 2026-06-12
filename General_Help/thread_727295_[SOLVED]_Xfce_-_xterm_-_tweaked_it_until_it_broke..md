---
title: "[SOLVED] Xfce - xterm - tweaked it until it broke."
date: 2008-03-17
forum: General Help
---

### Post by Bruce M. on 2008-03-17
OK, I tweaked it and now it's broken.

Xfce 7.10 comes with **xterm**, since I can't do cut and paste there easily I installed **Gnome Treminal**.

I was looking in  [Show us your .bashrc!]("http://ubuntuforums.org/showthread.php?t=679762") where I saw a rather nice terminal prompt so I asked how I could do it.

The [answer]("http://ubuntuforums.org/showpost.php?p=4520114&postcount=64") involved installing **zsh** ... which I did. Got the prompt but lost the custom aliases I'd made.

Before I learned how to create aliases in zsh I found [HOWTO: Customize terminal header]("http://ubuntuforums.org/showthread.php?t=674446")

So according to the answer in the first thread: executing 'chsh' and then enter '/bin/bash' to reverse it in Gnome Terminal I got my proper prompt back and aliases. So I deleted **zsh**

Opened xterm and see:
[CENTER][[IMG]http://img218.imageshack.us/img218/3117/screenshotyg6.th.png[/IMG]](http://img218.imageshack.us/my.php?image=screenshotyg6.png)[/CENTER]

OK, so I re-install zsh ... and do nothing else ... ie: executing 'chsh' and then enter '/bin/zsh'

and open both terminals to see:

[CENTER][[IMG]http://img127.imageshack.us/img127/6154/terminalste1.th.png[/IMG]](http://img127.imageshack.us/my.php?image=terminalste1.png)[/CENTER]

So again I execute 'chsh' and then enter '/bin/zsh' and I see the same thing as above.

Tried once more to get back to /bin/bash
```

bruloo% sudo chsh
Changing the login shell for root
Enter the new value, or press ENTER for the default
        Login Shell [/bin/zsh]: /bin/bash
bruloo% 

```

doesn't help, they are now both stuck at that prompt even after a [Ctrl]+[Alt]+[Backspace]

Please help!
I have no history, no aliases :(

How can I get my terminals back to normal, no zsh, and using /.bashrc again?

Bruce

---

### Post by jken146 on 2008-03-17
Middle mouse click pastes in xterm.  I can only help with this I'm afraid. :)

---

### Post by Bruce M. on 2008-03-18
> **jken146 said:**
> Middle mouse click pastes in xterm.  I can only help with this I'm afraid. :)

That is a GREAT tip.  **THANK YOU**

Now I can dump Gnome-Terminal
Bruce

---

### Post by Bruce M. on 2008-03-18
Hi folks, me again ...

I found a backup of the zsh config file so I have that working again (see attached)

But my question still applies:

How can I get my terminals back to normal, with no zsh, and using /.bashrc again?

Thanks
Bruce

---

### Post by Arthur Archnix on 2008-03-18
This may be a drastic solution, but apt-get remove --purge PROGRAM_NAME removes the program and associated config files. Then reinstall and it should be like new.

---

### Post by Bruce M. on 2008-03-18
> **Arthur Archnix said:**
> This may be a drastic solution, but apt-get remove --purge PROGRAM_NAME removes the program and associated config files. Then reinstall and it should be like new.

Still there ... doing Ctrl+Alt+Backspace.

Be right back
Bruce

---

### Post by Bruce M. on 2008-03-18
Hi...

Ctrl+Alt+Backspace shows that zsh is gone.

Gnome Treminal is using bash properly, **but**

When I open xterm and it displays:

```
xterm: Could not execute /bin/zsh: No such file or directory.
```

for 5 seconds and then disappears.

---

### Post by Bruce M. on 2008-03-20
Doesn't anyone know the answer to get xterm back to bash?

---

### Post by Bruce M. on 2008-03-28
Xterm is working properly and I have no idea why... but it is.  :)

The following is a series of emails I sent to a person found at one of the zsh sites on the web:

Hi Xxxxx,

I'm really new to Linux, so I'm not sure what all this is, but NOW it's working????

I opened xfce4-terminal called up xterm and it's using bashrc.
I can't figure it out, after 3 days; I send you an email, and now it works. It didn't work before writing you earlier today. And I turn my PC off at nights.

hmmmm, time to go to the doctor's office, I'll be in perfect health when I arrive. {joking}

But I am really puzzled here.

Thanks and have a nice evening,
Bruce

Xxxxx wrote:
> The problem is most likely that /etc/passwd isn't being re-read to
> look at your updated shell. Logging out of X and logging back in
> will almost definitely fix the problem.
>
> Good luck.
> - Xxxxx
>
> On Wed, Mar 26, 2008 at 04:31:05PM -0300, Bruce wrote:
>> Hi Xxxxx,
>>
>> One thing I can not find in the Workshop is how to delete zsh.
>>
>> I've done the chsh thing and changed it to /bin/bash
>>
>> This works great for xfce4-terminal (Xubuntu 7.10)
>> However xterm still uses it.  :(
>> Now when I do chsh in xterm it tells me the login shell is /bin/bash
>> If I remove zsh; xterm simply does not work, I get a blank flashing cursor.
>>
>> I would appreciate any advice you could give me to get xterm back to using my .bashrc file.
>>
>> Thank you.
>> Have a nice day.
>> Bruce Milmine

---

