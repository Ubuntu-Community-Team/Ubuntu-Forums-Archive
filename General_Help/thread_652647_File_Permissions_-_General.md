---
title: "File Permissions - General"
date: 2007-12-28
forum: General Help
---

### Post by flyboy_2003 on 2007-12-28
Has anyone seen the "@" symbol in file permissions before?

Like this:

-rw-r--r--@  1 root  root  size date file.name

If so, does anyone know what it means? I have googled it and come up with nothing.

Thanks.

---

### Post by p_quarles on 2007-12-29
It's a symbolic link. 
[http://en.wikipedia.org/wiki/Symlink](http://en.wikipedia.org/wiki/Symlink)

---

### Post by flyboy_2003 on 2007-12-29
> **p_quarles said:**
> It's a symbolic link. 
[http://en.wikipedia.org/wiki/Symlink](http://en.wikipedia.org/wiki/Symlink)

Where do you see that? A normal file looks like this:

-rwxrwxrwx   1 root root        35 2007-12-20 06:21 filename

A directory like this:

drwxrwxrwx   1 root root        35 2007-12-20 06:21 directoryname

And a symbolic link like this:

lrwxrwxrwx   1 root root        35 2007-12-20 06:21 filename1 -> filename2

The @ symbol referenced to in that Wikipedia page is 

"user@userbox". It means the current logged in user and the name of the host.

---

### Post by p_quarles on 2007-12-29
I'm not talking about the user@host lines on that page: "@" is the *nix designator for a symlink -- much like "/" means directory, "*" means executable, and so forth. 

If you don't believe me, try this (in your /home directory, otherwise you'll need to use sudo):
```
touch fakefile
ln -s fakefile fakelink
ls -F
```
You'll see a line that says "fakelink@".

---

### Post by flyboy_2003 on 2007-12-29
> **p_quarles said:**
> I'm not talking about the user@host lines on that page: "@" is the *nix designator for a symlink -- much like "/" means directory, "*" means executable, and so forth. 

If you don't believe me, try this (in your /home directory, otherwise you'll need to use sudo):
```
touch fakefile
ln -s fakefile fakelink
ls -F
```
You'll see a line that says "fakelink@".

OK, I see what you mean. The -F switch means "classify" and appends an indicator to the entry. However, this is following a file name. 

When I do a long listing (to show file permissions), the @ symbol does not show after the file name, it shows at the end of the permissions. Here's the actual file I am referring to:

-rw-r--r--@  1 root  wheel  5425123 28 Dec 23:16 Extras2.rsrc

This is actually a Unix file (Mac), but I thinking it's likely the same as in Linux (I use Ubuntu and OS X). 

When I do a man on ls in Mac, it says:

Display a slash (`/') immediately after each pathname that is a directory, an asterisk (`*')
after each that is executable, an at sign (`@') after each symbolic link, an equals sign (`=')
after each socket, a percent sign (`%') after each whiteout, and a vertical bar (`|') after
each that is a FIFO.

So when I do an ls -F on that file, I do NOT get an @ symbol. It just shows as a plain old file.

Any thoughts?

Thanks.

---

### Post by p_quarles on 2007-12-29
Yeah, I see what you're saying now. The placement of the "@" sign is where the sticky bit (a mostly deprecated permissions setting) usually goes. I did some looking, and I could not find any info on sticky bits being set to anything other than blank, "x", "t" or "T". So, I'm afraid I don't know what that means. 

If I had to guess, though, I would say that it is somehow related to a link (given that *nix is pretty consistent about naming conventions), but how that would work in the sticky bit is beyond me.

---

