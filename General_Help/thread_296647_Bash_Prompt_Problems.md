---
title: "Bash Prompt Problems"
date: 2006-11-09
forum: General Help
---

### Post by justin on 2006-11-09
I was recently trying to customize my bash prompt. Specifically, I was trying to recreate a prompt I have on a shell account running freebsd. Problem is, some of the characters that look fine when I ssh to the shell look garbled when I use them for my own prompt. Here is a picture of the problem:

[IMG]http://img370.imageshack.us/img370/1925/sslx6.png[/IMG]

What would be causing this?

---

### Post by po0f on 2006-11-09
justin,

Could you post what your PS1 declaration looks like?

---

### Post by justin on 2006-11-10
PS1='${debian_chroot:+($debian_chroot)}&#9484; &#9472;(\u@\h)\n&#9492;&#9472;(\w)-> '

---

### Post by stylishpants on 2006-11-10
Probably your shell's TERM environment variable is different.  

Try printing its value on the system where your fancy prompt works properly, and then on the other one.

You can print the value
```

echo $TERM

```

If they are different, try setting the value on the non-working system to match the working system.  

```

# notice that you don't use the $ in front of the var name when setting it
echo TERM="xterm"

```

---

### Post by justin on 2006-11-10
Doing the command echo $TERM on both systems returned 'rxvt'. The prompt works using the gnome terminal, but not with aterm. So I can conclude it's an aterm problem.

---

### Post by justin on 2006-11-10
Works under xterm too. ](*,)

---

### Post by justin on 2006-12-25
*bump*

I still want to use aterm (it works best with irssi in my opinion) but it still has trouble displaying certain characters. Here is an example of me connecting to an eggdrop.

[IMG]http://img368.imageshack.us/img368/5910/screenshotjustinmastersxe0.png[/IMG]

---

### Post by justin on 2006-12-25
Another example.

[IMG]http://img221.imageshack.us/img221/6871/screenshotjustinmasterscb6.png[/IMG]

---

### Post by po0f on 2006-12-25
justin,

I had a problem similar to yours.  The fix had something to do with ncurses; maybe try reinstalling it?

---

### Post by justin on 2006-12-26
Well, it doesn't seem that worked, unless I reinstalled ncurses incorrectly. Could you be a bit more specific on how to reinstall it? This is so frustrating, this is the only problem I've had with Ubuntu/Linux where I don't think I'll ever get it fixed. I'm actually quite surprised more people haven't had problems with this.

---

### Post by po0f on 2006-12-26
justin,

From Synaptic, just choose reinstall as the option for the package.  The package you're probably interested in reinstalling is [libncurses5](http://packages.ubuntu.com/edgy/base/libncurses5).

---

### Post by justin on 2006-12-26
Still nothing. Maybe some day I'll figure it out. ](*,)

---

