---
title: "command in path not found?"
date: 2013-03-05
forum: General Help
---

### Post by jremington on 2013-03-05
I'm running Xubuntu 12.04 and recently installed xvnc4viewer using the synaptic package manager. The executable is located in /usr/bin, which is my $path. However, I get "xvnc4viewer: command not found" when I type the program name into a terminal window. If I type /usr/bin/xvnc4viewer the program runs. So, why doesn't the automatic path search work?   Thanks, Jim Remington

---

### Post by prodigy_ on 2013-03-05
> **jremington said:**
> $path
It's $PATH, not $path. Use **echo $PATH** command to check.

---

### Post by jremington on 2013-03-05
Thanks but both variables $path and $PATH point to the same directories:  jims-dell:/> echo $PATH /usr/local/phenix-1.8.2-1309/build/intel-linux-2.6/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by rnerwein on 2013-03-05
hi
first forget "path" it's PATH !
where do you set your PATH - hope in your ~/.bashrc (if you have a bash as login shell).  be shure to set your PATH at the last line in your .bashrc.
type in a terminal: whereis your_program_you_search_for
and have a look at your program and type: file your_program_you_search_for
have a look of the given format of the file ( must be  ELF ....  LSB executable)
ciao

---

### Post by r-senior on 2013-03-05
What output do you get if you run this command?

```
which xvnc4viewer
```

---

### Post by jremington on 2013-03-05
Thanks guys.    >which xvnc4viewer yields "xvnc4viewer: command not found"   >whereis xvnc4viewers yields "/usr/bin/xvnc4viewer  /usr/bin/X11/xvnc4viewer"   >file /usr/bin/xvnc4viewer yields "xvnc4viewer: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x2b92ab1fc9ce35edb8e6fffef5da4981ca2828f3, stripped"   >echo $PATH yields "/usr/local/phenix-1.8.2-1309/build/intel-linux-2.6/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"  PS: is there some BBcode or setting I can use to maintain the line formatting of my response? Everything is run together.

---

### Post by r-senior on 2013-03-06
If you use the "Reply to Thread" button, rather than "Post Quick Reply", the edit window has a button marked with a "#" symbol. This will wrap selected text in code tags. For example:

```
which xvnc4viewer yields "xvnc4viewer: command not found"
whereis xvnc4viewers yields "/usr/bin/xvnc4viewer /usr/bin/X11/xvnc4viewer"
file /usr/bin/xvnc4viewer yields "xvnc4viewer: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x2b92ab1fc9ce35edb8e6fffef5da4981ca2828f3, stripped"
echo $PATH yields "/usr/local/phenix-1.8.2-1309/build/intel-linux-2.6/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

Once you've seen the "code" tags in a post, you can also enter them by hand. I'm assuming the second command was actually "whereis xvnc4viewer".

As far as the issue is concerned, the key seems to be that "which" doesn't find the program but "whereis" does.

*From man which*
> which returns the pathnames of the files (or links) which would be exe&#8208;
cuted in the current environment, had its arguments been given as  com&#8208;
mands  in a strictly POSIX-conformant shell.  [COLOR="#FF0000"]It does this by searching
the PATH[/COLOR] for executable files matching the names of the  arguments.  It
does not follow symbolic links.

*From man whereis*
> whereis locates source/binary and manuals sections for specified files.
The  supplied  names  are first stripped of leading pathname components
and any (single) trailing extension of the form .ext, for example,  .c.
Prefixes  of  s.   resulting  from  use of source code control are also
dealt with.  whereis then [COLOR="#FF0000"]attempts to locate the desired program  in  a
list of standard Linux places[/COLOR].

Perhaps you could try using the guest account on your machine and see if it works from there? If it does, I think that would indicate that the path ($PATH) in your account is the problem. There's nothing that I can see in your output that indicates that, so something else must be at work here.

Another suggestion would be to try re-installing the package.

```
sudo apt-get install --reinstall xvnc4viewer
```

---

