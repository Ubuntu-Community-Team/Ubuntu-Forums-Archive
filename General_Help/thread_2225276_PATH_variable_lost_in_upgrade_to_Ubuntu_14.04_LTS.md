---
title: "PATH variable lost in upgrade to Ubuntu 14.04 LTS"
date: 2014-05-20
forum: General Help
---

### Post by jkeenan on 2014-05-20
I have been using Ubuntu 13.10 LTS for the past month and today decided to upgrade to 14.04 LTS.  The upgrade appeared satisfactory until I attempted to use the Terminal application, as I customarily do for my software development work in Perl, Scala and other languages.  When I attempt, for example, to say:

###
vi .bashrc
###

I get this output:

###
Command 'vi' is available in '/usr/bin/vi'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
vi: command not found
###

Similarly, with other basic commands:

###
$ ls -l .
Command 'ls' is available in '/bin/ls'
The command could not be located because '/bin' is not included in the PATH environment variable.
ls: command not found
###

So it appears that this upgrade has wiped out my PATH environmental variable.  When I say,

###
echo $PATH
###

... all I get is:

###
/home/jkeenan/perl5/perlbrew/bin:/home/jkeenan/perl5/perlbrew/perls/perl-5.18.2/bin:
###

... which is merely the first two entries for PATH in my ~/.bashrc file.

How can I get directories such as /usr/local/bin, /usr/bin and /bin back into my PATH so that they are they're as soon as I open a Terminal?

Additional information:

When I say,

###
/bin/cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
###

... I see what I recall is a typical "default" path for Ubuntu systems.  I would expect these directories to be active in my $PATH at all times, even if I set other paths in my ~/.bashrc.  So another way of asking this is:  Why are the paths in /etc/environment not working?


Thank you very much.
Jim Keenan

---

### Post by Impavidus on 2014-05-20
What is the exact line you use to add things to the PATH in your .bashrc? And what is in your .profile?

---

### Post by jkeenan on 2014-05-20
I have partially discovered the source of my problem.

In my ~/.bashrc file, I have the following line:

#####
source ~/perl5/perlbrew/etc/bashrc
#####

perlbrew is a Perl extension which facilitates maintaining different versions of Perl 5 underneath one's homedir.  When one installs perlbrew, it writes the file cited above, which is then source-d into ~/.bashrc.  It appears that this sourced file, in effect, overwrites the value of $PATH set by /etc/environment.

I have for the time being commented out that 'source' line in my ~/.bashrc file.  In my .bashrc, I file, I prepend various bin directories underneath my homedir to the system-wide value of $PATH.  This gives me the PATH settings that I really want and enable me to use vi, ls, and all the other basic commands.

I will have to file a bug with the 'perlbrew' people, but this no longer appears to be fundamentaly a Linux or Ubuntu problem.

Thank you for reading this far.

Jim Keenan

---

### Post by Impavidus on 2014-05-21
Then you could modify the line in your ~/perl5/perlbrew/etc/bashrc that changes the PATH, so that it prepends things to your PATH instead of overwriting it. As you already prepend things to your PATH in your .bashrc you seem to know how to do that.

---

