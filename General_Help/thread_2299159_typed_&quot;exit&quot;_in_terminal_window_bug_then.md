---
title: "typed &quot;exit&quot; in terminal window: bug then impossible to login graphically at all"
date: 2015-10-16
forum: General Help
---

### Post by trigone on 2015-10-16
{note: there"s a typo in the title, i meant to write "terminal win(dow)"}

hi,

i got a seriously annoying and fully incapacitating problem. here's wa happened:

i typed in xfce4-terminal the command "exit", for the first time, to see wa wud happen (i was studying a linux or unix user guide). it's an old guide, and the command was said to theoretically end the X win sys if the command was entered in an xterm window.
i <enter>, and the terminal window disappears. i then try to open another one, thru a menu and also thru ctrl+alt+T, but i quickly realize tha in fact i can't open any window of any program anymore, although the windows of the previously opened programs are still visible and apparently usable.
typically, i decide to use the oldest repair method of history. i log out (graphically then) with the intent to log back in, so as to put things back in order, up and runnin. upon trying to log in though, the computer decides to bug me. everytime i enter my password then click on the "login" button, the screen turns black for a tiny fraction of second, then, the login screen reappears just like right before i entered my password and hit <enter>.
i checked, it doesn't do this when i give it a wrong password (plus my password is one char long so it's hard to make typo).

i hit ctrl+alt+F1, and actually managed to log in fine, but aside from this apparently it's impossible for me to access my session graphically.

since it's my only computer, i'm stuck with the guest session until i find a way to make it accept my login more than a fraction of second.

any idea, help, of any kind, is more than welcome, i'm not exactly up to the issue i'm facing. thanks a lot in advance.

have a nicer day than me ^^

---

### Post by deadflowr on 2015-10-16
I've edited the title for you.

Sometimes login loops, as they are known, happen because a certain file is corrupt.

When you log in via ctrl + a;t + F1 type
```
ls -la ~/.Xauthority
```
it should list your username.
If lists any other name, you'll need to change it
You can do so with
```
sudo chown username:username ~/.Xauthority
```

another thing to try is to move the file and reboot.
a fresh file will be generated.
to move
```
mv  ~.Xauthority ~.Xauthority.old
```
the reboot.

Hope it helps.

OH: and for future reference, if you have trouble with a thread or post, simply click on the report post button at the bottom of the post and the staff will gladly help fix the issue.

---

### Post by trigone on 2015-10-16
your first strategy worked perfectly, i can't thank you enough for your perfect and prompt answer! :D 

i'm curious as to how this bug happened. your [ls] test revealed tha my .Xauthority file had been apparently taken over by root.
do you reckon it was indeed provoked by my using the [exit] command, or was it just a big coincidence?

thanks again a lot! and thanks for the "future ref" tip, and the title editing too :)

---

### Post by deadflowr on 2015-10-16
The root change sometimes happens when using sudo on files or folders you already own.
Like if you copy or move a file you own to some place you also own like the command for move I posted, you will retain ownership.
But if you do the same but add sudo, then the new place you moved or copied that file will be owned by root.
If that makes sense.

Also, if you feel that the solution has worked for you, please mark this thread as solved.
So others might also benefit.
See: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by trigone on 2015-10-16
yes, i knew about this, but i didn't try to move or copy this very file as superuser ^^ not that i am aware of at least.

sure, i'll mark it as solved right away. thanks again!

---

### Post by ajgreeny on 2015-10-16
This type of problem can occasionally happen if you have used sudo to open a GUI application, eg **sudo gedit** or **sudo nautilus** and then carried out some operation to files or folders in your home.

**NEVER USE SUDO FOR GUI APPLICATIONS**

See Root-Sudo in my signature for details of how to use alternatives to sudo.

---

### Post by trigone on 2015-10-16
thank you ajgreeny! i'm gonna study this :)[[COLOR=#C61919]****[/COLOR]]("http://ubuntuforums.org/member.php?u=27747")

---

