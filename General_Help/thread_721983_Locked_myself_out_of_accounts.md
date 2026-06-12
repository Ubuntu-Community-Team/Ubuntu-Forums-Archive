---
title: "Locked myself out of accounts"
date: 2008-03-11
forum: General Help
---

### Post by Manolicious on 2008-03-11
I've got Fiesty 7.04

Here's the problem in a nut shell.  I have two user accounts with different passwords, one called "slave" and the other called "theater" that I use for a lot of non-work related stuff, mainly movies.  However I also tend to play games on my slave account, which I do to unhing myself from my work momentarily, while movie watching is a bit more of a commitment.  

I had trouble playing this one game on my slave account, and a person on a forum suggested I use a terminal command "sudo chown -R username. *" then "sudo chown -R username. ." in my home directory (which contains my slave and theater directories.  This worked great with the game, but I found myself unable to log into the theater account as it kept giving me the message 

"User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users."

So I set out to the IRC channel for ubuntu for help and people suggested I try using the theater name in the chown command instead of slave.  I tried this, but then I found I had reversed the problem, I could sign into theater, but couldn't get into slave which gave me the same .dmrc message.

I then looked through [ this thread]("http://ubuntuforums.org/showthread.php?t=91455")
 and a few other forums for answers to get back into my main account, and learned a command called chmod, and that I should use the command "chmod 644  .dmrc".  Some people suggested to use 700 instead of 644.  I tried this, experimenting in the theater, slave, and home directories, then I signed out.  Once I signed back into theater (after being again denied access to the slave account because of the .dmrc message) I then tried doing some of the same commands, but noticed I got a permission denied message if I tried to access the theater directory.  Then, programs started to close around me and I got kicked out of theater.  

Now I'm literally locked out of my computer.  I keep getting the .dmrc message with slave, and I just plain can’t get into theater.  I really don’t mind losing the theater account, but I really need to get back into my slave account.  

I still have the live cd with me if that’s any help.

PLEASE HELP!

---

### Post by amingv on 2008-03-12
This is what you did:

1. Open a console (presumably in /home/slave).
2. Typed sudo chown -R slave . -Made "slave" the owner of the current directory (/home/slave), not much of a problem.
3. Typed sudo chown -R slave .. -Now this is where it starts, let's notice some things:
    a. sudo: Super User DO
    b. chown: CHange OWNer
    c. -R: Recursively (including all subdirectories/files)
    d. slave: to this user
    e. this directory. Here is where death sings. '..' it's the parent directory of your current directory, thus /home
4. Command dutifully changes the owner of every file/folder in /home, including .dmrc.
5. User theatre tries to log-in, but he doesn't own the files in his home folder (or his home folder for that matter)

Possible fix:

1. Restart your computer in recovery mode (press ESC before Ubuntu starts loading and select "Recovery Mode" from the menu)
2. When you get to the command prompt, use the following commands:
```
chown root:root /home
chown -R slave:slave /home/slave
chown -R theatre:theatre /home/theatre
shutdown -r now
```
3. Computer will restart, try to log in and report back.
[COLOR="Red"]
***IMPORTANT***[/COLOR]
_Always_ make sure you know what a command does before typing it, especially if said command is preceded by "sudo".

---

### Post by Manolicious on 2008-06-28
Sorry it's been a while, but I have long since fixed the problem before receiving your advice.  Lucky two people in IT at my college campus are very well versed in Linux and were able to take care of my problem, though the solution they implemented doesn't sound as straightforward as the one you proposed.  

From what I remember, the .dmrc problem stopped us right at the sign-in screen, so he had to get to the command prompt using crtl-alt-F1.  I couldn't see all he had done, but it had something to do with a 3 or 5 digit number and he said what I had done was reassign one of those digits all to zero.  First he fixed my slave account, but he had to do something slightly different to get the theater account up and running.

For historical purposes, I've copied and paste my command line history here before I got locked out of both accounts as an example of what NOT to do with linux.  While in the file system, or “home” folder containing my user accounts; 

```

   58  sudo chown slave *

   59  sudo chown slave .

   60  ls

   61  sudo chown slave *

   62  sudo chown slave .

   63  sudo chown slave .dmrc

   64  sudo chown -R slave *

   65  sudo chown -R slave .

   66  ls

   67  cd ..

   68  ls

   69  chown -R slave .dmrc

   70  cd theater/

   71  ls

   72  chown -R slave .dmrc

   73  sudo chown -R slave .dmrc

   74  cd ..

   75  ls

   76  cd slave/

   77  ls

   78  sudo chown -R slave *

   79  sudo chown -R slave .

   80  cd ..

   81  ls

   82  cd slave/

   83  ls

   84  cd Desktop/

   85  ls

   86  cat ImportantCommands

   87  ls

   88  cd ..

   89  ls

   90  cd ,,

   91  cd ..

   92  ls

   93  sudo chmod 644 .dmrc

   94  sudo chown slave /.dmrc

   95  chown slave /.dmrc

   96  chown -R slave .dmrc

   97  sudo chown -R slave .dmrc

   98  ls

   99  cd ..

  100  ls

  101  sudo chown -R slave .dmrc

  102  chown -R slave .dmrc

  103  sudo chmod 755 /home/slave/

  104  ls

  105  sudo chmod 644 .dmrc

  106  sudo chown slave .dmrc

  107  ls .dmrc -l

  108  sudo chown theater .dmrc

  109  ls .dmrc -l

  110  cd theater/

  111  sudo chmod 644 .dmrc

  112  sudo chown slave .dmrc

  113  ls .dmrc -l

  114  cd ..

  115  cd slave/

  116  sudo chmod 644 .dmrc

  117  sudo chown slave .dmrc

  118  ls .dmrc -l

  119  cd ~

  120  ls

  121  sudo chmod 644 .dmrc

  122  sudo chown slave .dmrc

  123  sudo chmod 755 /home/slave 

  124  sudo chown slave /home/slave 

  125  ls

  126  cd ..

  127  ls

  128  sudo chown -R slave. *

  129  sudo chown -R slave. .

  130  sudo chown -R slave. *

  131  sudo chown -R slave. .

  132  ls

  133  chown -R slave .dmrc

  134  chown -R theater .dmrc

  135  ls .dmrc -l

  136  cd ..

  137  ls

  138  ls .dmrc -l

  139  cd slave/

  140  ls .dmrc -l

  141  sudo chmod 644 .dmrc

  142  sudo chown slave .dmrc

  143  ls .dmrc -l

  144  sudo

  145  sudo help

  146  sudo chmod 644 .dmrc

  147  bash sudo chmod 644 .dmrc

  148  cd ..

  149  ls

  150  sudo chmod 700 .dmrc

  151  cd slave/

  152  sudo chmod 700 .dmrc

  153  cd ..

  154  cd theater/

  155  sudo chmod 700 .dmrc

  156  history


```

After that last command I got kicked out of my theater account and couldn't enter either my slave or theater account after that.

---

