---
title: "search Command History"
date: 2013-02-23
forum: General Help
---

### Post by borgward on 2013-02-23
How do I search command history, besides using the up and down arrows?

For example I used a command that started with m, but I don't remember what that command was. I could up or down arrow thru several thousand commands until I recognize it. 

Is it possible search command history at a particular date?

---

### Post by howefield on 2013-02-23
Would you believe by using the history command ? :)

```
man history
```

---

### Post by nothingspecial on 2013-02-23
Hit Ctrl-R and start typing to search your bash history.

---

### Post by deadflowr on 2013-02-23
It's stored in the .bash_history file in your home folder.
Running history will show you everything listed in that file.

---

### Post by mc4man on 2013-02-23
You can also just use a .inputrc file either globally or locally in your home folder.
(i'm a single user so just add to home folder.

```
gedit .inputrc
```
For searches based on letter(s) typed in terminal using the page up/down keys
```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```

if wanting to use the arrow up/down instead for All searches (with nothing typed searches as usual - last command > back/foward, with something typed uses that instead

```
"\e[A": history-search-backward
"\e[B": history-search-forward
```

---

### Post by schragge on 2013-02-23
> **borgward said:**
> For example I used a command that started with m, but I don't remember what that command was.In bash
```
fc -l m m
```

---

### Post by stinkeye on 2013-02-23
Same as **mc4man's** tip except to say the setting to bind "page up" and "page down" to search the history
already exists in the system wide **/etc/inputrc** file.
Just need to uncomment.

ie
```
gksudo gedit /etc/inputrc
```
and uncomment lines 41 and 42 to look like...
```
# alternate mappings for "page up" and "page down" to search the history
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```

---

### Post by borgward on 2013-03-03
> **nothingspecial said:**
> Hit Ctrl-R and start typing to search your bash history.
 $ Ctrl Shift R (you did mean capitol R?)
(reverse-i-search)`': m
(reverse-i-search)`m': cat .bash_history | more

I am looking for a way to search history for commands starting with m

---

### Post by borgward on 2013-03-03
> **schragge said:**
> In bash
```
fc -l m m
```

That is only getting me one instance of the letter m.  I want to see all the commands in history that start with m.

---

### Post by stinkeye on 2013-03-03
> **borgward said:**
> $ Ctrl Shift R (you did mean capitol R?)
(reverse-i-search)`': m
(reverse-i-search)`m': cat .bash_history | more

I am looking for a way to search history for commands starting with m

mc4man's solution does what you want.
eg bind pgeup/down to
```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```

Enter one ore more characters for the start of the command then
press pageup to cycle back through your history for commands you've used
starting with those characters.

---

### Post by borgward on 2013-03-03
> **stinkeye said:**
> mc4man's solution does what you want.
eg bind pgeup/down to
```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```

Enter one ore more characters for the start of the command then
press pageup to cycle back through your history for commands you've used
starting with those characters.

13:58:24 abc@1520: ~$ "\e[5~": history-search-backward
\e[5~:: command not found
13:59:08 tom@1520: ~$ 
13:59:14 abc@1520: ~$ "\m[5~": history-search-backward
\m[5~:: command not found
13:59:31 abc@1520: ~$ "\e[5~":m  history-search-backward
\e[5~:m: command not found

Can you run the command on your machine and show me the results? What version are you running?

---

### Post by steeldriver on 2013-03-03
Are you typing those commands literally on the command line? you need to  open (or create) your ~/.inputrc **file **and **paste **those bindings in to it  (or uncomment the global bindings by editing /etc/inputrc)

```

$ cat ~/.inputrc
# alternate mappings for "page up" and "page down" to search the history
"\e[5~": history-search-backward
"\e[6~": history-search-forward

```

then you will be able to use the PgUP / PgDn **keys **to search

NB you will also need start a new shell so it re-reads the bindings

---

### Post by borgward on 2013-03-03
Edited /etc/.inputrc with gedit as follows:

# alternate mappings for "page up" and "page down" to search the history
  "\e[5~": history-search-backward
  "\e[6~": history-search-forward

Opened new terminal


14:32:00 tom@1520: ~$ "\e[5~": history-search-backward
\e[5~:: command not found
14:36:09 tom@1520: ~$ m "\e[5~": history-search-backward
m: command not found
14:36:19 tom@1520: ~$ "\m[5~": history-search-backward
\m[5~:: command not found
14:36:39 tom@1520: ~$ m"\e[5~": history-search-backward
m\e[5~:: command not found
14:39:15 tom@1520: ~$ "\e[5~": m history-search-backward
\e[5~:: command not found

---

### Post by Cheesemill on 2013-03-03
Another solution is to set up an alias in your ~/.bashrc file, I have the following line in mine...
```
 alias hist='history | grep'
```
I can then use this new hist command to search for a text string in my history, for example...
```
rob@raring:~$ hist VB
   81  VBoxHeadless --startvm Gateway --vrde off &
   83  VBoxHeadless --startvm Gateway --vrde off &
  100  VBoxHeadless --startvm Gateway --vrde off &
  111  VBoxManage setproperty autostartdbpath /etc/vbox
  112  VBoxManage modifyvm --autostart-enabled on
  113  VBoxManage modifyvm Gateway --autostart-enabled on
  164  VBoxHeadless --startvm gw --vrde off &
  167  VBoxHeadless --startvm gw --vrde off &
  174  VBoxHeadless --startvm gw --vrde off &
  176  VBoxHeadless --startvm gw --vrde off &
  178  VBoxHeadless --startvm gw --vrde off &
  184  VBoxHeadless --startvm gw --vrde off &
  194  VBoxHeadless --startvm gateway --vrde off &
  200  VBoxHeadless --startvm gateway --vrde off &
  269  hist VB
rob@raring:~$ 
```

---

### Post by stinkeye on 2013-03-03
> **borgward said:**
> Edited /etc/.inputrc with gedit as follows:

# alternate mappings for "page up" and "page down" to search the history
  "\e[5~": history-search-backward
  "\e[6~": history-search-forward

Opened new terminal


14:32:00 tom@1520: ~$ "\e[5~": history-search-backward
\e[5~:: command not found
14:36:09 tom@1520: ~$ m "\e[5~": history-search-backward
m: command not found
14:36:19 tom@1520: ~$ "\m[5~": history-search-backward
\m[5~:: command not found
14:36:39 tom@1520: ~$ m"\e[5~": history-search-backward
m\e[5~:: command not found
14:39:15 tom@1520: ~$ "\e[5~": m history-search-backward
\e[5~:: command not found

Read posts 5 & 7
The two lines given bind keys to the history-search command by editing the **inputrc** config file.
They are not terminal commands.
Add them to **~/.inputrc**  to apply just for you.
Uncomment them in **/etc/inputrc** to apply for all users.

All you need to do now is close any terminal you have open
then open a new terminal and enter your search term.
eg type in  **m** and press pageup to cycle back and pagedown to cycle forwards through your
history of commands starting with **m**.

---

### Post by drmrgd on 2013-03-03
Maybe could also pipe history to a grep with a regex if you are looking for something with little info.  For example, in your case, since you only know it started with an 'm':

```
history | grep -E '[[:digit:]]\s m'
```

For me, scrolling through the history even with those scroll tricks that others have posted is more of a pain than just grepping out what I'm looking for.

---

### Post by Rebelli0us on 2013-03-03
> **borgward said:**
> $ Ctrl Shift R (you did mean capitol R?)
(reverse-i-search)`': m
(reverse-i-search)`m': cat .bash_history | more

I am looking for a way to search history for commands starting with m


Reverse search still eludes me, not sure it's possible in Linux, but I'm used to it from using 4NT. 

[Here is my complete .inputrc]("http://ubuntuforums.org/showthread.php?t=1711499&p=12422432#post12422432") with Command History Recall   and in-place Filename Completion

---

### Post by markbl on 2013-03-20
I just read through this thread and realised nobody has mentioned this. The commands described here are for the bash emacs line editing mode. Due to some historical quirk, the emacs mode is the default but given that by far and away most people use vi (i.e. vim on linux) instead of emacs then they really are better off using the same vi commands for line editing, i.e. add a "set -o vi" in your ~/.bashrc to change bash to use vi mode. In this mode you press ESC to change to edit mode, press k to go back a line, j to go forwards, / to search, etc. See man bash.

Also, most linux commands that provide a command line interface use the readline library so if you add "set editing-mode vi" to your ~/.inputrc (create it if it does not exist) then you will get the loveliness of vi line editing in all those apps.

---

### Post by tommpogg on 2013-04-09
Hi,
I am using Xubuntu 12.04.
I have modfied the .inputrc file in my home directory with the commands suggested above but nothing has changed.
I can't search the history with up/down arrows.
I have also tried to modify /etc/inputrc but I have obtained tha same negative result.

In the past I have used this trick in Ubuntu and it worked fine.
What is happening?
Do Ubuntu and Xubuntu behave differently? Do they use different shells?

Thank you

---

### Post by markbl on 2013-04-09
> **tommpogg said:**
> 
I have modfied the .inputrc file in my home directory with the commands suggested above but nothing has changed.
I can't search the history with up/down arrows.

Is this post responding to mine just above? Did you change your ~/.bashrc as I said? (that's the important part!) Note that my post is about changing the default emacs command history editing mode to vi editing mode, is that what you want to do?

If yes to all the above, then make sure you log out and back in after editing your ~/.bashrc. Then use the normal vi editing command to edit your command line, i.e. press ESC to enter edit mode, press 'k' to go up, 'j' to go down, etc (or use the arrow keys if you want to move around suboptimally - just as in vi). Any confusion then do as I said in my post, read about vi edit mode in man bash.

---

