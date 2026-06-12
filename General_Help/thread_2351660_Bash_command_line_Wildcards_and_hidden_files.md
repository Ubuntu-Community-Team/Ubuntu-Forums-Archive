---
title: "Bash command line: Wildcards and hidden files"
date: 2017-02-05
forum: General Help
---

### Post by AwaitingUserInput on 2017-02-05
I am trying to write a backup script that will copy all hidden files directiories and the hidden subdirectories in my home folder. I do NOT want to copy anything that is not hidden.

This is what I tried, and it copied my entire home directory, both the hidden and visible files:

```
[FONT=monospace][COLOR=#000000]rsync -avh --delete --progress /home/myusername/.* /tmp/hidden-home_files/[/COLOR]
[/FONT]
```

I thought that maybe the "[COLOR=#000000][FONT=monospace]/home/myusername/.*" part expanded to mean the same thing as ./all_My_Files_and_Folders

So I tried it like this:
[/FONT][/COLOR]```
[FONT=monospace][COLOR=#000000]rsync -avh --delete --progress /home/myusername/\.* /tmp/hidden-home_files/[/COLOR]

[/FONT]
```

I thought that the "\" character would let the shell know that I really did only want to copy anything whose filename starts with a "." and not everything in the home directory, but it copied everything anyways.

Why is it doing this and how can I fix it?

Thank you.

---

### Post by papibe on 2017-02-05
Hi AwaitingUserInput.

Both of your examples do the same.

The problem you have is that .* will match . (dot), which will match /home/myusername/. , i.e., /home/myusername/, in other words: everything.

To reference only hidden files and directories you need to use a little more complex regular expression. Try this in your home directory:
```
echo .*

echo .[^.]*

echo .!(|.)
```
The second one would work most of the time, but it is not perfect (unlikely files like ...abcd won't match).

Considering that, this should be the best approach:
```
rsync -avh --delete --progress /home/myusername/.!(|.) /tmp/hidden-home_files/
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by AwaitingUserInput on 2017-02-05
Thank you for the help, but it's still not working correctly.

When I typed 

```
$ [FONT=monospace][COLOR=#000000]echo .!(|.)[/COLOR]
[/FONT]
```

In my home directory as you advised, it gave me the list of hidden files that we are looking for. However, when I ran my backup script with rsync, it gave the following error:

```
[FONT=monospace][COLOR=#000000]./fullbackup: line 22: syntax error near unexpected token `('[/COLOR]
./fullbackup: line 22: `rsync -avh --delete --progress /home/username/.!(|.) /mnt/backup/Home-Hidden_files'
[/FONT]
```

Any other ideas?

---

### Post by Keith_Helms on 2017-02-05
Try this
```

[FONT=monospace][COLOR=#000000]shopt -s dotglob
rsync -avh --delete --progress /home/myusername/[.]* /tmp/hidden-home_files

```[/COLOR]
[/FONT]

---

### Post by papibe on 2017-02-05
```
./fullbackup: line 22: syntax error near unexpected token `('
./fullbackup: line 22: `rsync -avh --delete --progress /home/username/.!(|.) /mnt/backup/Home-Hidden_files'
```
I believe you just pasted the command as it was. Try using your actual username instead of the literal string 'username'.

Let us know how it goes.
Regards.

---

### Post by HermanAB on 2017-02-06
The way to think about it is that a '*' includes a '.' and therefore a '.*' includes a '..' which means the previous directory in the tree.

So then you can see why it goes wonky.

---

### Post by AwaitingUserInput on 2017-02-06
> **papibe said:**
> ```
./fullbackup: line 22: syntax error near unexpected token `('
./fullbackup: line 22: `rsync -avh --delete --progress /home/username/.!(|.) /mnt/backup/Home-Hidden_files'
```
I believe you just pasted the command as it was. Try using your actual username instead of the literal string 'username'.

Let us know how it goes.
Regards.

No, I did put my actual username and then changed it for the forum post.

If it helps, I am editing the script in Kate (kde's text editor) which marks up bash scripts automatically. There is unexpected markup in the problematic line. It looks like this:

[SIZE=4][COLOR=#00ff00]rsync[/COLOR] -avh --delete --progress /home/user/.!(|[COLOR=#00ff00].[/COLOR]) [COLOR=#00ff00]/mnt/backup/Home-Hidden_files

[/COLOR][SIZE=1]Actually, the color is blue, not green, but the green is more visible on this forum so I changed the color. The final '.' character is colored, as well as the [/SIZE][/SIZE][SIZE=1]final path and the command "rsync."[/SIZE]

---

### Post by steeldriver on 2017-02-06
IIRC the extglob (extended globs) bash shell option is only enabled by default in interactive sessions - in a script, you may need to set it explicitly e.g.

```

#!/bin/bash

shopt -s extglob

*rest of script*

```

---

### Post by papibe on 2017-02-06
Good catch steeldriver :)

---

### Post by AwaitingUserInput on 2017-02-06
Yep, I added the "shopt -s extglob" line to the beginning of the script and it copied the way it's supposed to.

Thanks everyone for the help!

I'll mark the thread as "solved"

---

