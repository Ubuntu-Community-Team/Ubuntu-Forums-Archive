---
title: "Run programs as a different user?"
date: 2014-04-23
forum: General Help
---

### Post by lunix2 on 2014-04-23
Is there a way to run Kmail and Korganizer and Akdodani (which they depend upon) as a user different than the one who is logged into KDE?  I'd like to be able to do this with other things like MySql as well.

I am trying to get away from Windows, which handles my eMail and other stuff easily.  But I have to be able to run certain things as a different user in order to make it work.

Many thanks for your help.

Bill

---

### Post by jamesisin on 2014-04-23
It may be possible to run certain GUI apps via the command line as a different user (by telling the system which tty receives the window).  I would be hard pressed to imagine a scenario where that would be the best solution, however.  Can you tell us a little more about why you want to do things in this particular manner?  Perhaps we can come up with a better solution for you.

---

### Post by SeijiSensei on 2014-04-23
Yes, it's possible, but tell us what you want to do first.

Most programs in Linux run either as the "root" (administrative) user, or as the user logged into the session.  However, some programs, mostly ones that run on servers, are launched by root, but then spawn a "child" process which is run as a different user.  MySQL is one such program.  The mysqld daemon is launched by root, but the active process runs as user "mysql" in group "mysql".  The Apache web server runs as user "www-data" in Debian/Ubuntu.

Partly this is a consequence of the rule that only root can run a program that attaches to a TCP or UDP "port" numbered between 0 and 1023.  Since web services run on port 80, a web server must start up as root.  However that program is really just a stub that spawns a set of children running as www-data.  That means that malicious web requests cannot reach the actual system.

There is no reason I can think where ordinary desktop programs need to be run as someone other the original user.  Maybe you had reasons for doing this in Windows, but "Linux is not Windows" and implements an entirely different security model.

---

### Post by dave97232 on 2014-04-24
I am sure there are other ways, but one is to use the "su" command.  Open a command line terminal to run the following examples.

First, type the command whoami.  It will print your login name:

**[FONT=courier new]whoami[/FONT]**

Okay, now let's run that command under a different user name.  Substitute the other account name for john:

**[FONT=courier new]su john -c whoami[/FONT]**

First it will ask for the password for account john.  Then you will see the output of whoami as from account john.  Now let's try a more complicated example with command line arguments.  You need to quote the entire command.  Also, if there are quotes inside, you need to escape them.  Try the following example:

**[FONT=courier new]su john -c "echo \"I am running as `whoami`\""[/FONT]**

So there is a mechanism.  The su command might fail if you run it from some place other than a command terminal (such as a menu or some other kind of program launcher).  An alternative is ssh.  You may need to install the package named ssh to get it.

Then try this:

**[FONT=courier new]ssh john@localhost echo "\"I am running as `whoami`\""[/FONT]**

Those options work from the command terminal.  Now if you want to edit a launcher command in a menu or something else, you have that pesky password prompt to deal with.  There are ways to deal with it but they are too complicated for my post.  i suggest you explore what google brings up.

---

### Post by HermanAB on 2014-04-24
Well, that is what su and sg are for.  Read the nice man pages for details.

---

### Post by lunix2 on 2014-04-24
I oringally created this thread: [http://ubuntuforums.org/showthread.php?t=2219148](http://ubuntuforums.org/showthread.php?t=2219148), which was closed by a well-meaning admin.  The policy he pointed me to clearly indicates what the forum policy is, and even has  examples that show that the post was okay.  Here's the policy: [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

So I had to ask my question in a less elegant and more confusing way.

Thanks very much for your answers.

I will say that though kdesu works,it requires a separate terminal session for each process that is spawned, since it sits and waits for the return code.  I can find no way around that.  Othwerwise I'd write a script to switch to my dedicated virtual desktop, spawn some processes as root, and switch back tto the first desktop at login time (as I login as a regular user for kmail and other apps).

---

### Post by lunix2 on 2014-04-24
Thanks to all, and Herman too.

---

### Post by lunix2 on 2014-04-24
The bottom line:  If I could open one terminal session and spawn more than one program as root without waiting for any of those to shut down and return their success value, I'd have my problem solved.

And for the first time ever I would not need to consider logging in as root to do everything.

Initially I wanted to login as root, then- on a separate desktop- launch some programs (like a browser and Email and orgainizer) as me (they don't work well with root login anyway.  But the other approach where I login as me and spawn the other processes as root is better and safer.

As of now, I can't quite get either method to work well enough to automate the process.

---

### Post by anaconda on 2014-04-24
Those commands only work, if the "other" user is root.

I would like to run firefox as another user (who is NOT root)

Is that possible.?

The reason: 
I have a separate user for connecting to bank etc.  Now I have to logout and login if I want to do that.

(Yeah. I know. I could also just have a separate profile in firefox, and then the cache, cookies  etc. would also be 
separate, which is good for safety)

---

### Post by bapoumba on 2014-04-24
Closed for review.

---

