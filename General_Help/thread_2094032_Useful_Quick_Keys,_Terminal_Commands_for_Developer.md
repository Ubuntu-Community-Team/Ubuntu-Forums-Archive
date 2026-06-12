---
title: "Useful Quick Keys, Terminal Commands for Developers?"
date: 2012-12-12
forum: General Help
---

### Post by MusicalRobots on 2012-12-12
Hi Guys,

Excuse me if this is too general, but I wanted to start a thread for my own pleasure.  I've been using Ubuntu for about two years now.  I'm a full time software developer, I code for fun, profit and to make gifts for the grilfriend.  I think I am more or less proficient, though not an expert by any means.  I can generally get anything I want to done - though not always done well.

What I'm looking for are quick key combos, terminal commands, or other nifty tricks/tools to make my use more efficient.  I'm hoping some of you guru's who've been using Ubuntu as a development environment since you were young whippersnappers like myself could weigh in and share your favorite efficiencies. 

Thanks guys,

-Robots

---

### Post by drmrgd on 2012-12-12
Wow, where to start.  Depending on what you're doing at the time and the types of things you do, there's tons and tons of quickie shortcuts and tricks.  I guess the most general and useful at the moment is manipulating the history.  Of course, issuing 'history' will bring up the commandline history.  However, for really quick things there are various shortcuts.  Issuing '!!' repeats the very last command executed.  This is extremely helpful for cases (which just happened to me a few minutes ago) where you forgot to 'sudo' a command.  I was altering a system file just now, forgot that it was a system file and issued:

```
vim <filename>
```

Rather than retyping the whole thing (because it was actually a long path I was following in this case), and rather than hitting the up arrow and modifying the line, all I had to do was:

```
sudo !! 
```

If you want to repeat some other command further back in the history, you can use !<command_history_number>.  Say you ran a command a few lines ago (or even days ago) and want to re-run it.  You can get there really quickly by following something like this:

```
$ history | grep samtools #search the history for something with samtools in it
2066  for f in *.bam; do echo "$f: $(samtools view -c -F 4 $f) reads" >> samplekey.txt; done
$ !2066

```

That will quickly run that command again for you.  

Now let's say you need to alter the command a little by changing a word (you misspelled something or just want to change a filename or something), you can use a substitution in conjunction:

```
!!:gs/<original>/<change>/
```
That will re-run the very last command, globally changing the <original> to <change>.  So, let's say that I want to change the command I showed above to use as part of the output "Sample #6 Reads: " instead of just "reads" (which is an actual command I ran yesterday), I can do something like:

```
$ !2066:s/reads/Sample #6 Reads: "/
for f in *.bam; do echo "$f: $(samtools view -c -F 4 $f) sample #6 reads: " >> samplekey.txt; done

```

That will re-run that command with the simple change and I've saved my wrists a large amount of typing.  

Also, along those lines, you can do a quick substitution on the last command (this is can not be made global like the example I showed above), you can do something like:

```
$ ls mdia
ls: cannot access mdia: No such file or directory
[2]$ ^mdia^media^
ls media
floppy  floppy0
```

There's a few nifty tricks for exploiting history to work through the command line a little more quickly.

---

### Post by MusicalRobots on 2012-12-12
drmrgd,

Thanks!  Exactly the sort of things I was looking for.  I've actually been wondering if there were good ways to use the history for this sort of thing for awhile now but hadn't looked into it.  Fantastic!

I'll start playing with those today.

Just found cntl-r which is a nice version of this, thought wihout the pleasant display and ability to call by history number.  Nice alternative never the less.

---

### Post by Habitual on 2012-12-12
Robots:

My Personal Favorites:
```
vim + ~/.bashrc
``` and add
 ```
bind '"\e[A": history-search-backward'
bind '"\e[B": history-search-forward'
``` save and exit
 ```
source ~/.bashrc
``` Now in terminal type <previous_cmd> and press the Up Arrow key and if the first 'hit' isn't "the one", press Up Arrow until it is. Went past it you say, Down Arrow key.
They are processed in ***REVERSE ORDER***... where "previous_cmd" is either an entire or partial previously used command in ~/.bash_history.

```
vim ~/.vimrc
``` and add:
```
au BufWritePost * if getline(1) =~ "^#!" | if getline(1) =~ "/bin/" | silent !chmod a+x <afile> | endif | endif
``` now every file you "vim" and the file has [COLOR=Red]***any***[/COLOR]  shebang (perl, awk, bash, !#any/thing) will have the e**x**ecute flag when you exit vim.
[B]-rwxr-xr-x 1 jj users 12 Dec 12 2012  4:35 PM robots.txt

[/B]Have fun!

---

### Post by drmrgd on 2012-12-12
> **Habitual said:**
> Robots:

<snip>
```
vim ~/.vimrc
``` and add:
```
au BufWritePost * if getline(1) =~ "^#!" | if getline(1) =~ "/bin/" | silent !chmod a+x <afile> | endif | endif
``` now every file you "vim" and the file has [COLOR=Red]***any***[/COLOR]  shebang (perl, awk, bash, !#any/thing) will have the e**x**ecute flag when you exit vim.
[B]-rwxr-xr-x 1 jj users 12 Dec 12 2012  4:35 PM robots.txt

[/B]Have fun!

Nice one!  I never thought to do that.  That's definitely getting added to my vimrc!

By the way, if you're a vim user (both of you), have a look at nerdCommenter and supertab.  I can't live without nerdCommenter; it allows you to very quickly comment out chunks of code, along with my favorite function: copy a line to the buffer, and comment out the one that's there.  The you can just use 'p' to drop the original in place.  If you want to just try a change on one line of code but want to keep the original line, this is a very quick way to do it.  Supertab allow tab completion of items like variables, which is handy in long scripts where you start to forget the exact spelling of a variable you used.  Helps keep compile mistakes down for me at least!

---

### Post by MusicalRobots on 2012-12-13
@Habitual

Nice one.  I'm adding that now.

Quick question:

Do you guys keep lists of useful things you've found, or do you derive them as you need them based on through understanding of the systems in place?  Or is the question kind of a silly one?

-Robots.

---

### Post by MG&amp;TL on 2012-12-13
> **MusicalRobots said:**
> 
Do you guys keep lists of useful things you've found, or do you derive them as you need them based on through understanding of the systems in place?  Or is the question kind of a silly one?


Depends on whether the things I find are good or bad. If they're good (i.e. new hints and tips), I tend to integrate them into my workflow enough that I remember them.

If they're bad (i.e. this feature won't work on Ubuntu 11.x), it tends to be painful enough that I remember it. :mad:

---

### Post by Cheesemill on 2012-12-13
My top tip is to make use of aliases.

Create yourself a ~/.bash_aliases file and fill it full of useful things, here's mine:

```
rob@arch:~$ cat .bash_aliases 
alias sudo='sudo '
alias pacman='pacman-color'
alias update-grub='sudo grub-mkconfig -o /boot/grub/grub.cfg'
alias vi='vim'
alias ipl='get_iplayer --nocopyright'
alias gipl='get_iplayer --nocopyright --output=/home/rob/Videos --tvmode=flashhd,flashvhigh,flashhigh,flashstd,flashnormal --get'
alias hist='history | grep'
alias paci='sudo pacman -S'
alias pacu='sudo pacman -Syyu'
alias pacr='sudo pacman -R'
alias pacs='pacman -Ss'
alias sv='sudo vim'
alias df='df -h -t ext4'
alias du='du -h --max-depth=1 | sort -hr'
alias ls='ls -lh --color=auto'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias msf='sudo /opt/metasploit/msfconsole'
alias pg='ps -Af | grep $1'
```

I also have /root/.bash_aliases symlinked to /home/rob/.bash_aliases so that they stay in sync between both accounts for when I'm logged into a root shell using 'sudo -i'.
Some of my aliases are Arch specific so they won't be any use on your Ubuntu machine but you get the general idea.

---

### Post by MusicalRobots on 2012-12-17
Hey Cheese,

Thanks for that one.  The CD and ls aliases are a nice idea.  

Robots.

---

### Post by m_duck on 2012-12-17
I symlink my ~/.bashrc too. Anything that is only wanted for your user, *or* root, rather than globally can be dealt with using an if statement along the lines of:
```
if [ $(id -u) -eq 0 ]; then
   # root-specific stuff
else
   # (any) user-specific stuff
fi
```(I *think* this is right - not at a Linux machine at present).

Where ***id -u*** returns the uid of the current user (will be 0 if root and something else, either 500+ or 1000+ for a normal user, in most distros I think).

It can be useful for using different colours for your PS1, or having equivalent commands with (or without) sudo added for example.

---

### Post by Cheesemill on 2012-12-17
Yep, I use that technique in my symlinked .bashrc to give different coloured prompts for normal (green) and root (red) shells.

```
if [ `id -u` != "0" ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
fi

```

---

