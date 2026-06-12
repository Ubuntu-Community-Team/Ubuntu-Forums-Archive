---
title: "Find And Delete Empty Subdirectories"
date: 2022-05-17
forum: General Help
---

### Post by wyattwhiteeagle on 2022-05-17
How can I find empty subdirectories and delete them?

It takes a lot of time to go through my personal private folders on the Desktop looking for empty folders that I don't need anymore.

GUI is ok but I prefer CLI commands for doing this.

---

### Post by Holger_Gehrke on 2022-05-18
```

find ~ -type d -empty

```

should produce a list of all empty directories under your $HOME.

Holger

---

### Post by HermanAB on 2022-05-19
Hmm, don’t automate a delete script too much, due to the risk of something going wrong.

The suggestion above of making a list in a file and then checking the list carefully before doing something stoopidttt is best.

---

### Post by Impavidus on 2022-05-19
The **rmdir** command can only remove empty directories. Not much that can go wrong then.

---

### Post by wyattwhiteeagle on 2023-01-31
What went wrong here?
I was attempting to find and delete empty subfolders within a directory on the Desktop.

```
find && rmdir /home/wyatt/Desktop/L7MC-Cut-Textures -type d -empty
find && rmdir /home/wyatt/Desktop/L7MC-Room-Textures -type d -empty
find /home/wyatt/Desktop/L7MC-Cut-Textures -type d -empty > /home/wyatt/Desktop/L7MC-Cut-Textures.txt
find /home/wyatt/Desktop/L7MC-Room-Textures -type d -empty > /home/wyatt/Desktop/L7MC-Room-Textures.txt

```
I formulated the above as a script and ran it with sudo

Terminal printed the following...

```
wyatt@wyatt-latitudee5400:~$ sudo /home/wyatt/Desktop/L7MC-Empty-Folders.sh > /home/wyatt/Desktop/L7MC-Empties-Report.txt
[sudo] password for wyatt:           
rmdir: invalid option -- 't'
Try 'rmdir --help' for more information.
rmdir: invalid option -- 't'
Try 'rmdir --help' for more information.
wyatt@wyatt-latitudee5400:~$ 

```

---

### Post by Impavidus on 2023-01-31
You can't just string commands together and expect the shell to guess how they have to be connected. In your case, you first ran the find command without any arguments, which won't do anything useful. It printed all files and directories in your current directory, recursively, which was redirected to your log. When that was successful, you ran the rmdir command with some directory as an argument and some options which rmdir doesn't know, so it gave an error. This error was pinted to stderr, so it wasn't redirected to your log. The directory and the options were meant to be arguments for find, which also needs rmdir as an argument so that find can run rmdir on the empty directories it finds.

Read some examples on find. That command can best be learned from examples.

---

### Post by Holger_Gehrke on 2023-01-31
'sudo' shouldn't have been necessary; you're searching inside your $HOME and the directories should all be accessible to you.

'find'-commands follow the pattern 'find <where to start the search> <options describing what to search for> <options describing what to do with found stuff>' (this is very simplified; actually everything you give to find is evaluated as a logical expression with implied 'AND' between parts which don't have an explicit logical operation between them; you can do some really amazingly complex stuff with find, which of course means it can be dangerous ...). In the first two commands in your script you're running find without arguments or options, which means 'find everything under the current working directory and print it'. If 'find' doesn't produce an error (which it won't) it's running 'rmdir' with options meant for 'find' which 'rmdir' doesn't understand. The other two lines should have worked and written to the files ~/Desktop/L7MC-Cut-Textures.txt and ~/Desktop/L7MC-Room-Textures.txt.

 If I was trying something like this, I'd end up with 'find /home/wyatt/Desktop/L7MC-Cut-Textures /home/wyatt/Desktop/L7MC-Room-Textures -type d -empty -print0|xargs -0 rmdir'. This searches for empty directories starting from each of the two directories you give and prints them out with the items being separated with 0x00 (that's the only character which absolutely can't be part of a file name). 'xargs' reads from standard input, using those 0x00 bytes as separators (that's what the '-0' option means; yes, that's a zero, not a capital 'o') and calls the program given with the stuff it has read as arguments. Doing it this way has some advantages, especially if there are filename containing spaces or other unusual characters. Alternatively I could have used the '-delete' action of 'find' or the action '-exec rmdir \{\} \;' (yes, all those backslashes are necessary; without them the shell will use up those braces and the semicolon and remove them without find getting to see them, which would be bad).

Holger

---

### Post by wyattwhiteeagle on 2023-01-31
> **Impavidus said:**
> You can't just string commands together and expect the shell to guess how they have to be connected. In your case, you first ran the find command without any arguments, which won't do anything useful. It printed all files and directories in your current directory, recursively, which was redirected to your log. When that was successful, you ran the rmdir command with some directory as an argument and some options which rmdir doesn't know, so it gave an error. This error was pinted to stderr, so it wasn't redirected to your log. The directory and the options were meant to be arguments for find, which also needs rmdir as an argument so that find can run rmdir on the empty directories it finds.

Read some examples on find. That command can best be learned from examples.

Thank you for that.

You can't just assume that someone just strings commands together without doing some research before doing so.
Well, I did that.
Before I just "strung commands together", I pulled up the Find Manual...you know...the
```
man find
```
Do you realize that the "-type d" in that script isn't even mentioned except in an example in that manual, but "-type c" is explained in detail?

The invalid option that the terminal informed me of...that option appears nowhere in the commands that I ran as a script, even though it directed me to rmdir help.

In fact, the commands that I ran are a compilation of commands which are spread across 5 or 6 linux scripts, as well as from the examples in the Find Manual.

---

### Post by wyattwhiteeagle on 2023-01-31
> **Holger_Gehrke said:**
> 'sudo' shouldn't have been necessary; you're searching inside your $HOME and the directories should all be accessible to you.

'find'-commands follow the pattern 'find <where to start the search> <options describing what to search for> <options describing what to do with found stuff>' (this is very simplified; actually everything you give to find is evaluated as a logical expression with implied 'AND' between parts which don't have an explicit logical operation between them; you can do some really amazingly complex stuff with find, which of course means it can be dangerous ...). In the first two commands in your script you're running find without arguments or options, which means 'find everything under the current working directory and print it'. If 'find' doesn't produce an error (which it won't) it's running 'rmdir' with options meant for 'find' which 'rmdir' doesn't understand. The other two lines should have worked and written to the files ~/Desktop/L7MC-Cut-Textures.txt and ~/Desktop/L7MC-Room-Textures.txt.

 If I was trying something like this, I'd end up with 'find /home/wyatt/Desktop/L7MC-Cut-Textures /home/wyatt/Desktop/L7MC-Room-Textures -type d -empty -print0|xargs -0 rmdir'. This searches for empty directories starting from each of the two directories you give and prints them out with the items being separated with 0x00 (that's the only character which absolutely can't be part of a file name). 'xargs' reads from standard input, using those 0x00 bytes as separators (that's what the '-0' option means; yes, that's a zero, not a capital 'o') and calls the program given with the stuff it has read as arguments. Doing it this way has some advantages, especially if there are filename containing spaces or other unusual characters. Alternatively I could have used the '-delete' action of 'find' or the action '-exec rmdir \{\} \;' (yes, all those backslashes are necessary; without them the shell will use up those braces and the semicolon and remove them without find getting to see them, which would be bad).

Holger

Very informative and explanitory.

There was a time when someone mentioned that sudo isn't needed in the command.
When I ran the command without sudo...the terminal informed me that though sudo isn't needed, I get more detailed info if I use sudo.
So I just automatically run scripts with sudo unless I know for certain that using sudo will break something.

I haven't ran into that bad luck since using a command to change permissions to root and caused me to have to do a fresh clean install.
lol...haven't made that stupid move since then.
When it comes to testing a backup...that's not such a stupid move...but I wasn't testing a backup.

I'll explore with this and report back here with what happens

Thanks a bunch.

---

### Post by The Cog on 2023-01-31
Just to explain the problem with ```
find && rmdir /home/wyatt/Desktop/L7MC-Cut-Textures -type d -empty
```
The && in a bash command means "and then, if that command succeeded, do", so that it:
- runs the command find, with no arguments (this will always succeed), and when that's finished,
- runs the command rmdir with 4 arguments. The first arg is a folder and I guess this would have worked except the second argument "-type" looks like options "-t -y -p -e" and rmdir doesn't understand all of them so it bails out.

I think the command you are looking for is ```
find -type d -empty -delete
```

---

### Post by wyattwhiteeagle on 2023-01-31
> **The Cog said:**
> Just to explain the problem with ```
find && rmdir /home/wyatt/Desktop/L7MC-Cut-Textures -type d -empty
```
The && in a bash command means "and then, if that command succeeded, do", so that it:
- runs the command find, with no arguments (this will always succeed), and when that's finished,
- runs the command rmdir with 4 arguments. The first arg is a folder and I guess this would have worked except the second argument "-type" looks like options "-t -y -p -e" and rmdir doesn't understand all of them so it bails out.

I think the command you are looking for is ```
find -type d -empty -delete
```

I don't want to delete all empty folders in my /home directory.
Where in this command would the specified location be inserted?

---

### Post by Holger_Gehrke on 2023-01-31
Well, in this case using the script with 'sudo' is actively harmful since it creates files owned by root (the log files ...). With the default umask this is not a problem (the file is created with 644 permission - "rw-r--r--") but if you have set a different umask you could end up having to use sudo to read the files. Unnecessary use of sudo breeds more use of sudo ... 

The program telling you that you get more information with 'sudo' was probably something like 'lshw' or 'lsusb'. Those can read information only accessible as root when called with sudo and make do with what's available to them when not. They are special cases. Normally you should not use sudo unless you know you need to and understand the reasons for it and the implications of doing so. I spend a lot of time on the command line and rarely use sudo more than once or twice per day.

> 
Do you realize that the "-type d" in that script isn't even mentioned  except in an example in that manual, but "-type c" is explained in  detail?

You are mis-reading the explanation
```
-type _c_
              File is of type _c_:

              b      block (buffered) special

              c      character (unbuffered) special

              d      directory

              p      named pipe (FIFO)

              f      regular file

              l      symbolic  link;  this  is  never  true if the -L option or the -follow option is in effect, unless the symbolic link is broken.  If you want to search for symbolic
                     links when -L is in effect, use -xtype.

              s      socket

              D      door (Solaris)

              To search for more than one type at once, you can supply the combined list of type letters separated by a comma `,' (GNU extension).


```
'c' is a placeholder for a character with that character being one of 'b','c','d','f','l','s', and 'D'. You can tell it's a placeholder because it's underlined. All placeholders in this manual page are underlined.

Holger

---

### Post by The Cog on 2023-01-31
> **wyattwhiteeagle said:**
> I don't want to delete all empty folders in my /home directory.
Where in this command would the specified location be inserted?

The starting point defaults to the current directory. If you specify a starting point, it must be the first argument. Either of these should do the trick:

```
cd ~/Desktop/L7MC-Cut-Textures
find -type d -empty -delete
```
```
find ~/Desktop/L7MC-Cut-Textures -type d -empty -delete
```
I agree with Holger_Gehrke - I would be **very** nervous about using sudo to delete stuff outside my home folder with a script. It's only a few months since I had to spend a few days rebuilding my work laptop because of exactly that. It was only supposed to delete inside a specific deeply nested folder, but it escaped and deleted /* because of an unfortunate typo.

---

### Post by wyattwhiteeagle on 2023-01-31
> [COLOR=#000000]The starting point defaults to the current directory. If you specify a starting point, it must be the first argument. Either of these should do the trick:[/COLOR]

[COLOR=#000000]Code:
cd ~/Desktop/L7MC-Cut-Textures
find -type d -empty -delete[/COLOR]
[COLOR=#000000]Code:
find ~/Desktop/L7MC-Cut-Textures -type d -empty -delete[/COLOR]
[COLOR=#000000]I agree with Holger_Gehrke - I would be [/COLOR]**very nervous about using sudo to delete stuff outside my home folder with a script. It's only a few months since I had to spend a few days rebuilding my work laptop because of exactly that. It was only supposed to delete inside a specific deeply nested folder, but it escaped and deleted /* because of an unfortunate typo.**

> [COLOR=#000000]You are mis-reading the explanation[/COLOR]
[COLOR=#000000]Code:
-type _c_
              File is of type _c_:

              b      block (buffered) special

              c      character (unbuffered) special

              d      directory

              p      named pipe (FIFO)

              f      regular file

              l      symbolic  link;  this  is  never  true if the -L option or the -follow option is in effect, unless the symbolic link is broken.  If you want to search for symbolic
                     links when -L is in effect, use -xtype.

              s      socket

              D      door (Solaris)

              To search for more than one type at once, you can supply the combined list of type letters separated by a comma `,' (GNU extension).[/COLOR]
[COLOR=#000000]'c' is a placeholder for a character with that character being one of 'b','c','d','f','l','s', and 'D'. You can tell it's a placeholder because it's underlined. All placeholders in this manual page are underlined.[/COLOR]

Thank yall
Explaining the Find info helped a lot, cleared up some confusion.

Both code's more than likely work well.
I chose the 1-line command.
Worked awesome
```
find ~/Desktop/L7MC-Cut-Textures -type d -empty -delete
```
With all the sudo info here, I believe I need to be a bit more cautious when using sudo.

---

### Post by TheFu on 2023-01-31
> **Impavidus said:**
> The **rmdir** command can only remove empty directories. Not much that can go wrong then.

+1.  I use this fact constantly. Multiple times a day.

---

### Post by wyattwhiteeagle on 2023-01-31
```
find ~/Desktop/L7MC-Cut-Textures -type d -empty -delete
```
There are times when deleting an empty folder leaves the parent folder empty.
Is there a way to have the command run more than once on the specified location without having to enter the command more than once?

About rmdir in this case...
I more than likely had the command in an incorrect order as indicated above.
The find and delete command worked.

---

### Post by TheFu on 2023-01-31
Press the up-arrow.  Amazing?

You can also use select/paste, if you are using X/Windows.
Anytime we select anything, it is placed into the x-buffer.  Paste the selection using the middle-mouse button.  There are short-cuts for selections when you want the selection to be full words or full lines.  Double-click and drag to select a word at a time.  Triple-click to get a full line. Whenever I see someone right-clicking to get a context menu, then selecting copy, I cringe a little.  They are doing it the hard way.  If selecting anything takes over 1 second, you are doing it the hard way.

Anyway, if you use a proper editor, put the single command line into the editor.  Type 'y' (yank), then type '5p' to paste the yank'ed line 5 times.  You have a script now.  Save the file and run it with 
```
$ sh ./file-you-saved
```
If it takes over 10 seconds to edit, you are doing it the hard way.

You'd only need to re-run the command the number of times the depth of the directories.  I'd be surprised if 5 times wasn't sufficient.  It you  like, run it 100 times.

---

### Post by wyattwhiteeagle on 2023-01-31
> **TheFu said:**
> Press the up-arrow.  Amazing?

You can also use select/paste, if you are using X/Windows.
Anytime we select anything, it is placed into the x-buffer.  Paste the selection using the middle-mouse button.  There are short-cuts for selections when you want the selection to be full words or full lines.  Double-click and drag to select a word at a time.  Triple-click to get a full line. Whenever I see someone right-clicking to get a context menu, then selecting copy, I cringe a little.  They are doing it the hard way.  If selecting anything takes over 1 second, you are doing it the hard way.

Anyway, if you use a proper editor, put the single command line into the editor.  Type 'y' (yank), then type '5p' to paste the yank'ed line 5 times.  You have a script now.  Save the file and run it with 
```
$ sh ./file-you-saved
```
If it takes over 10 seconds, you are doing it the hard way.

You'd only need to re-run the command the number of times the depth of the directories.  I'd be surprised if 5 times wasn't sufficient.
From the info, just repeat the line how ever many times you want it to run?
And, since it's a script now, will it run without using sudo, or is sudo required to run scripts?

---

### Post by The Cog on 2023-02-01
From memory, in the man page for find, deleting directories implies something like depth-first, so it knows to work from bottom up. Check the manual. Try on a small test directory.

---

### Post by Impavidus on 2023-02-01
From the man page for rmdir:```
       -p, --parents
              remove  DIRECTORY  and  its ancestors; e.g., 'rmdir -p a/b/c' is
              similar to 'rmdir a/b/c a/b a'
```

---

### Post by TheFu on 2023-02-01
> **wyattwhiteeagle said:**
> From the info, just repeat the line how ever many times you want it to run?
And, since it's a script now, will it run without using sudo, or is sudo required to run scripts?

Did you just try it and learn the answer?  That's what I'd expect.

---

### Post by wyattwhiteeagle on 2023-02-03
> **TheFu said:**
> Did you just try it and learn the answer?  That's what I'd expect.
yep
with a little tweaking of that command line...it worked.

rmdir is a safer option

---

