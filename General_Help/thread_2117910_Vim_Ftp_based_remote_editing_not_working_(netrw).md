---
title: "Vim Ftp based remote editing not working (netrw)"
date: 2013-02-19
forum: General Help
---

### Post by powerslave12r on 2013-02-19
Maybe someone here could help me out with a problem I'm having over ftp.

Environment:
- Lubuntu 12.10 (64), also Lubuntu 12.04 (64), Ubuntu 12.04 (64), Linux Mint 13 (64).
- LXterminal, UXTerm and gnome-terminal
- GVim/Vim 7.3.547, 7.3.429
- both passive and active ftp
- a local ftp server using filezilla and [http://secureftp-test.com/](http://secureftp-test.com/) to test it.

When I try to access a remote ftp directory, I can only open the directory that I typed in a path to. As soon as I navigate through the listed directories and hit enter on any, the screen splits into two horizontal panes and the top pane reads "File not found".

I tried this from Windows 7 Gvim/Vim (don't have the version handy but it was 7.3+) and it worked as expected.

From what I gather it just doesn't seem to look for the right directory after I hit enter in the list I think. Maybe it skips an extra forward slash somewhere or something?

I can't seem to figure out what the issue is. I am going to try running the same thing off of an Ubuntu and Mint Live CD and see if it persists. 

If so, sadly I'm going to have to either replace Lubuntu or look at remote editing alternatives to ftp.

Would greatly appreciate your help! :)


EDIT: Tried it out with Mint 13, Ubuntu 12.10 and 12.04 with same results.

I must be doing something terribly wrong.

---

### Post by jwbrase on 2013-02-19
I have sshd running on my machine and can sftp to localhost with vim and read files. Using vim to ftp to the site you linked, I get the error you described with some files but not with others (hamlet.xml opens fine, for instance).

---

### Post by powerslave12r on 2013-02-19
Hey hwbrase, thanks for checking it out. I don't seem to have a problem with reading files, but I do with navigation of directories.

For example:

I can successfully do

```
:e ftp://test@ftp.secureftp-test.com:21//subdir1/
```

But when I do 

```
:e ftp://test@ftp.secureftp-test.com:21//
```

And hit enter after selecting the 'subdir1' for example, is when I get that error.

I have not once successfully performed this navigation.

I tried installing different versions of netrw, fresh vim installs, many live CD variants of debian based distros but with the absolute same result.


The only reason I presume I'm not chasing smoke is because this thing works under windows 7 like a charm. And I doubt it's a 'windows handles this in a non conventional way' sort of a thing. This is supposed to be expected behavior.


As an aside, the reason why I'm so hellbent on finding a solution is because at work, we use a Linux host and ftp into Windows Virtual Machines and work with code.

Everyone uses jEdit, whose ftp plugin, I might add, is epic. I'm a huge fan of jEdit, but I've just been getting addicted to vim more and more over time and now I can't do without it.

Any other solutions to handle this setup? Any help appreciated. :)

Thanks!

---

