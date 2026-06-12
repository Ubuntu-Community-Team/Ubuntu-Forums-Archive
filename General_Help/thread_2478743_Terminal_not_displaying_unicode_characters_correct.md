---
title: "Terminal not displaying unicode characters correctly"
date: 2022-09-04
forum: General Help
---

### Post by Paddy Landau on 2022-09-04
I am having a [serious problem]("https://github.com/borgbackup/borg/issues/6999") on my Ubuntu 22.04, installed just 7 days ago. The thing is that I cannot reproduce this error on a VM installation of either 20.04 or 22.04, nor can other people on their machines.

It's to do with Python not dealing with unicode characters.

What I seem to have narrowed it down to is a symptom that my terminal (gnome-terminal) doesn't deal with unicode characters in file names or contents.

Now, I don't know if this has any relation to the other problem, but I'd like to fix this anyway, and then see if makes a difference to my original problem.

I have a file named [FONT=courier new]borgé[/FONT] (note the unicode character). This is what happens in my terminal in the VM, where it works correctly:
```
$ ls -l
-rw-rw-r-- 1 paddy paddy 10 Sep  4 13:02 borgé
$ cat borgé   # Using tab to autocomplete the file name
...
```
This is what happens on my main machine, where it doesn't work correctly. Note that, strangely, tab to autocomplete works fine.
```
$ ls -l-rw------- 1 paddy paddy 10 Sep  4 13:01 'borg'$'\303\251'
$ cat borgé   # Using tab to autocomplete the file name
...
```
The same is true in the console (Ctrl+Alt+F3); the VM works fine, and my main machine shows this strange output.

As I say, this might have nothing to do with my original problem, but it would be nice to fix this to see if it makes a difference.

More information:

[LIST]
[*]I do not have an alias on [FONT=courier new]ls[/FONT]
[*]LANG=en_GB.UTF-8
[*]LC_CTYPE=en_GB.UTF-8
[*]LANGUAGE=en.UTF-8
[*]I have run [FONT=courier new]sudo select-default-wordlist[/FONT] and selected [FONT=courier new]british-english[/FONT].
[*]Running [FONT=courier new]dpkg-reconfigure -plow locales[/FONT] shows both [FONT=courier new]en_GB.UTF-8 UTF-8[/FONT] and [FONT=courier new]en_US.UTF-8 UTF-8[/FONT] marked.
[*]I have run [FONT=courier new]locale-gen en_GB.UTF-8 en_US.UTF-8[/FONT].
[*]I have run [FONT=courier new]sudo update-locale LANG=en_GB.UTF-8 LANGUAGE=en.UTF-8[/FONT]
[/LIST]
Can you tell me what's going on, and what I can do to fix it, please?

---

### Post by Paddy Landau on 2022-09-04
… And I've just discovered the problem!

I had [FONT=courier new]LC_ALL=C[/FONT]. When I unset [FONT=courier new]LC_ALL[/FONT], my terminal works fine.

Ugh.

---

