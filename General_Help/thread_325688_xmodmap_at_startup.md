---
title: "xmodmap at startup"
date: 2006-12-26
forum: General Help
---

### Post by Hiroshima on 2006-12-26
Looking over the posts that come up with an xmodmap search, I see other people are wanting to do similar things that I want to do.

I want  ```
xmodmap -e "keycode 51 = bracketright braceright kana_MU kana_closingbracket"

``` to run at startup.  

If I understand right, I should just make a ~/.xmodmaprc file (I assume I should use gedit for this), and put the above code line in the file.

That didn't seem to do anything, so I listed > xmodmaprc in the Systems>Prefernces>Sessions>Startup Programs list, but it still doesn't seem to work.

I must be missing something.  Any ideas?

Thank you, Hiroshima

---

### Post by bulldog on 2006-12-26
Did a little forum searching, and here's what I found:

Create a new text document. Paste this in and save it to your home directory:

```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"  (or what ever you want of course)
```


Then right-click the file, and click the "Executable" check boxes.

Now you'll need to move the file into /usr/bin - the easiest way to do that will be through Terminal (as you need permissions to write to the directory):

Code:

sudo mv filename /usr/bin


Then go to your System menu > Preferences > Sessions > Startup programs and add your file to the list.

---

### Post by HadroLepton on 2006-12-26
you don't need to put that file in /usr/bin. in fact i advise against that because you will just unnecessarily clutter your system. linux has a strong multi user tradition and therefore allows  almost anything to be customized by users, no need for root or sudo.

now to the xmodmap problem:
for this command
```
xmodmap -e "keycode 51 = bracketright braceright kana_MU kana_closingbracket"
```
you should write
```
keycode 51 = bracketright braceright kana_MU kana_closingbracket
```

read here for more: [http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html](http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html)

put those lines in a file named **.xmodmaprc** in your home and it should be read everytime you login.

---

### Post by Hiroshima on 2006-12-26
Thank you bulldog and HadroLepton.  I try when I get home, and then let you know how it works!

Thanks,

Hiroshima

---

### Post by Hiroshima on 2006-12-27
> **HadroLepton said:**
> 
now to the xmodmap problem:
for this command
```
xmodmap -e "keycode 51 = bracketright braceright kana_MU kana_closingbracket"
```
you should write
```
keycode 51 = bracketright braceright kana_MU kana_closingbracket
```

put those lines in a file named **.xmodmaprc** in your home and it should be read everytime you login.

Brilliant!

Works like a charm!

Thank you.

Hiroshima

---

### Post by wasert on 2007-01-06
hi

I tried the same procedure, but my .xmodmaprc file is not being read.

When I type the following code, my keys are remapped correctly.

```
xmodmap -e "keycode 115 = dead_tilde"
xmodmap -e "keycode 109 = dead_acute"
```

Contents of my .xmodmaprc (located in my home directory):

keycode 109 = dead_acute
keycode 115 = dead_tilde

I am using Xubuntu Edgy. Could that be the problem?

Thanks in advance for your help

---

### Post by Hiroshima on 2007-01-25
Sorry I didn't reply for so long... I didn't see the post. Since I was getting help with this, I can't offer any new advice, but I hope this reply gets your question bumped up a bit.

hiroshima

---

### Post by RedSquirrel on 2007-01-29
> **wasert said:**
> hi

I tried the same procedure, but my .xmodmaprc file is not being read.

When I type the following code, my keys are remapped correctly.

```
xmodmap -e "keycode 115 = dead_tilde"
xmodmap -e "keycode 109 = dead_acute"
```Contents of my .xmodmaprc (located in my home directory):

keycode 109 = dead_acute
keycode 115 = dead_tilde

I am using Xubuntu Edgy. Could that be the problem?

Thanks in advance for your help


I'm not sure if you're still looking for an answer to this, but all you have to do is rename your .xmodmaprc file to .Xmodmap and it will be loaded at startup.

If you look in /etc/gdm/Xsession, you will see this:

```

usermodmap="$HOME/.Xmodmap"
```That's why the file should be named .Xmodmap instead of .xmodmaprc.

---

