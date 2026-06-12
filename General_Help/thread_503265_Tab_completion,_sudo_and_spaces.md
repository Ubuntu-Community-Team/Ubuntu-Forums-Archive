---
title: "Tab completion, sudo and spaces"
date: 2007-07-17
forum: General Help
---

### Post by Nephiel on 2007-07-17
I'm using Dapper 6.06 LTS and I'm wondering why the shell tab completion doesn't work when used with sudo and a file name which contains spaces. Let me show you what happens:

I create two test files:
```
myself@mymachine:~/Desktop$ touch foo.txt
myself@mymachine:~/Desktop$ touch bar.txt
myself@mymachine:~/Desktop$ ls
bar.txt
foo.txt
```
Then I try to move one to the other using tab completion:
```
myself@mymachine:~/Desktop$ mv f(tab) b(tab)
```
which yields
```
myself@mymachine:~/Desktop$ mv foo.txt bar.txt
myself@mymachine:~/Desktop$ ls
bar.txt
```
I create the first file again, and try to move it like before, but this time using sudo (I type the password when sudo asks for it):
```
myself@mymachine:~/Desktop$ touch foo.txt
myself@mymachine:~/Desktop$ ls
bar.txt
foo.txt
myself@mymachine:~/Desktop$ sudo mv f(tab) b(tab)
```
the tabs expand into
```
myself@mymachine:~/Desktop$ sudo mv foo.txt bar.txt
myself@mymachine:~/Desktop$ ls
bar.txt
```
Works fine, so I am sure tab completion is enabled for sudo. Now let's create another test file with spaces in the filename:
```
myself@mymachine:~/Desktop$ touch foo\ with\ spaces.txt
myself@mymachine:~/Desktop$ ls
bar.txt
foo with spaces.txt
```
Trying to move it without sudo and using tab completion:
```
myself@mymachine:~/Desktop$ mv f(tab) b(tab)
```
it becomes
```
myself@mymachine:~/Desktop$ mv foo\ with\ spaces.txt bar.txt
myself@mymachine:~/Desktop$ ls
bar.txt
```
So far, so good. But if I create the same file and try to sudo and move it:
```
myself@mymachine:~/Desktop$ touch foo\ with\ spaces.txt
myself@mymachine:~/Desktop$ ls
bar.txt
foo with spaces.txt
myself@mymachine:~/Desktop$ sudo mv f(tab) b(tab)
```
the second (tab) does not expand, leaving me with
```
myself@mymachine:~/Desktop$ mv foo\ with\ spaces.txt b
```

What's more, as a user, if I press (tab) two times at this point, it will show me a list of the files in ~/Desktop/ so I can choose one, but with sudo it just doesn't happen.

I'd swear this worked before, but I can't figure out when it stopped working or what has changed... It's a bit annoying. I can use tab completion when sudoing, or with filenames which contain spaces, but not both.

---

### Post by brent113 on 2007-07-17
This may be a bash bug.  Since bash isn't in it's final state, you might look around the bug boards.  I donno, just a suggestion.

---

### Post by Mr. C. on 2007-07-17
Works fine for me, but I have the latest version of bash.

Do you have any complete commands ?

```
$ complete
```

MrC

---

### Post by Mr. C. on 2007-07-18
Ok, I've figured out the problem.

The knucklheads here at Ubuntu have created a bunch of bash completion workarounds for sudo.

There is a file /etc/bash_completion, which has the line:

```
complete -F _root_command $filenames sudo fakeroot really
```

Bash auto-completion can be configured to do almost anything, like complete a list of commands for you after you type sudo [tab] and then filenames, etc.

Their complete _root_command does not work correctly when there are escaped spaces.

If you comment out the above line, and start a new shell, your autocompletion works again.

I'm not going to spend time debugging that monstrosity they've created, so I'll leave that to some young, enterprising lad.

MrC

---

### Post by Nephiel on 2007-07-31
Commenting out that line in /etc/bash_completion worked perfectly. Thanks a lot!

---

