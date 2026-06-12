---
title: "Howto: Install PHP5 easily"
date: 2005-06-24
forum: General Help
---

### Post by bcorcoran on 2005-06-24
Granted, PHP5 is unsupported due to "stability issues" (which I find ridiculous, but anyway, moving on!).

Here is ALL the steps you need to know to get php5 installed via apt.

1. Get to a terminal (or if you have no window system, you're set -- like me!)

--from now on, i will just assume you know that basically whenever i just list a command as a step, you'll type it--
-- "#" means root btw (and don't type the # or $ symbol!); use sudo if you didnt set up your root password -- 

2. **# nano /etc/apt/sources.list**
3. Scroll down using the arrow keys or pgup/pgdn and when you find the lines that start with "deb http://....", add the following line:

[B]deb [http://www.backports.org/debian](http://www.backports.org/debian) stable ucf
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5 woody
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5 woody[/B]

Now, press Ctrl+O, then press Enter, then press Ctrl+X (this saves the file, confirms the name, and then exits nano)

3. **# apt-get update**
4. **# apt-get install php5**
5. Ignore the message about the package not being authenticated. It's not from the ubuntu sources, thats why it comes up with it.

6. You're done!

---

### Post by dcatdemon on 2005-07-06
I would like to add that just recently, there seem to be a hoary section in dexter's php5 repository.  Hence, if you are interested, you could replace the dexter's debian section in your sources.list with this:

[B]deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5 hoary
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5 hoary[/B]

The good thing about this is that you **can** now use php5 with apache2  ;-) , the guide above to retrieve from woody, while excellent, only means that you could use php5 with apache1.x because it only has libapache-mod-php5, whereas the hoary section contains libapache2-mod-php5 and resolves the relevant dependancies.

and yes, I know about the other method of compiling from source, I'm just lazy...:p.

Hope this helps.

---

### Post by dizzie on 2005-07-07
Sorry to break the fun, but... apt-getting php5 like this overrides apache2 and install apache 1.3.33  ](*,)

---

### Post by dcatdemon on 2005-07-11
Not really.  I **could upgrade** from apache 1.3.3 to 2 actually because of the new hoary addition to the dexter's deb repository.  Otherwise, I was stuck with 1.3.3

---

### Post by MadMan2k on 2005-07-18
meanwhile breezy is supported too - works fine with apache2

---

### Post by djensen47 on 2005-07-24
I tried the instructions as described above using the "hoary" settings. But it does not seem to work. After I restarted apache2 I tried a test.php file that I wrote and the browser tried to download the file. It's almost as if the php extension was not registered.

And I solved my problem. Not knowing what to do I went into Synaptic to see what other packages might be needed and sure enough there were more php5 packages. Here is the list of what I installed to get things working ...

libapache-mod-php5
php5-mysql

There are several other php5 packages too.

---

### Post by spiderworm on 2005-07-29
huh? get my hopes all up and then there's no amd 64 bit packages?  what did i ever do to you? ;)

---

### Post by bpilgrim1979 on 2005-07-29
[Example 4.1](http://us3.php.net/manual/en/install.unix.php)  of the PHP installation docs works fine for Hoary and Apache 1.3.  installation from source.

---

### Post by sirsean on 2005-07-31
Okay, this all worked and got me running PHP and cooperating with Apache. However, I'd like to run a Postgresql database, and it's not working for me. I've installed Postgres, and when I try to install the php5-pgsql package, it tells me it needs libpgsql but it's not installable. A search for libpgsql shows that it's nowhere to be found in the apt-get repository.

What do I do about this? Thank you.

---

### Post by viniosity on 2005-08-03
I added dexter's repo and installed libapache2-mod-php5 and php5-mysql which brought a few other packages too.  But, when I checked my phpinfo page it still shows that I'm using PHP4.3.10-10ubuntu4.  

When I tried to remove php4 I got this

```

apt-get remove php4
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libphp-adodb php4 phpmyadmin
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.

```

I'd very much like to keep my phpmyadmin working and I know that I need lib-php-adodb for flyspray.  Is there a workaround for this?  How can I make sure I'm using php5 and not 4 if I have both installed?

---

### Post by mgor on 2005-08-15
to use this php5 package with apache2 you've to install libapache2-mod-php5 first.
```
$ sudo apt-get install libapache2-mod-php5
$ sudo apt-get install php5
```

---

### Post by .M@ on 2005-09-05
Thanks mgor. Do you know which repository libapache2-mod-php5 is in? I've checked the universe and multiverse...
Thanks, M@

---

### Post by Cellophan on 2005-09-06
I found this thread just few weeks ago. Very interesting and usefull. But I reinstall my distibution and I realise that the repository has been closed.

Where can I get those packages ?

Dexter if you read this... pleeeeeease ;)

---

### Post by Norman Cardinal on 2005-09-06
[QUOTE=Cellophan]I found this thread just few weeks ago. Very interesting and usefull. But I reinstall my distibution and I realise that the repository has been closed.

Where can I get those packages ?

Dexter if you read this... pleeeeeease ;)[/QUOTE]

Try using the new sources listed here:

[http://people.debian.org/~dexter/dists/php5.0/](http://people.debian.org/~dexter/dists/php5.0/) 

it looks like things have just been changed around a bit:

# PHP5.0 for Ubuntu hoary
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary

I hope that helps!

Norm.

---

### Post by ggnore on 2005-09-08
Hello.

I used your tutorial to install php5.
I also installed prado which is a framework.

The problem is that php5 seems to not be working correctly : i have a problem with sessions.

I m not sure, but i think that the php5 that is on the dexter repository is compiled without sessions management ...



[QUOTE="http://localhost/prado/examples/phonebook.php"]Fatal error: Call to undefined function session_id() in /var/www/prado/framework/TSession.php on line 132[/QUOTE]

---

### Post by Heitzso on 2005-09-08
[QUOTE=Norman Cardinal]Try using the new sources listed here:

[http://people.debian.org/~dexter/dists/php5.0/](http://people.debian.org/~dexter/dists/php5.0/) 

it looks like things have just been changed around a bit:

# PHP5.0 for Ubuntu hoary
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary

I hope that helps!

Norm.[/QUOTE]
 Dexter php5.0 repository not picking up ... Sept 8 05, error message:

"Couldn't stat source package list [http://people.debian.org](http://people.debian.org) php5.0/hoary Packages (/var/lib/apt/lists/people.debian.org_%7edexter_dists_php5.0_hoary_binary-i386_Packages) - stat (2 No such file or directory)"

My sources.list
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary

---

### Post by Cellophan on 2005-09-09
[QUOTE=Norman Cardinal]Try using the new sources listed here:

[http://people.debian.org/~dexter/dists/php5.0/](http://people.debian.org/~dexter/dists/php5.0/) 

it looks like things have just been changed around a bit:

# PHP5.0 for Ubuntu hoary
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary

I hope that helps!

Norm.[/QUOTE]
Thx ! It works well !

---

### Post by Adam (NZ) on 2005-09-27
Thanks to all in this thread ... I installed PHP5 without a hitch :cool:. Didn't even need to edit a single ini file. I was utterly gobsmacked when phpinfo() just fired up!!

I've installed PHP a fair few times now (from v3 upwards, Linux & Win32) and this had to be the easiest!

:p Adam :p

---

### Post by ergi1075 on 2005-09-30
Hi, I must be missing something, can someone help?

Starting with a working Apache2/PHP 4 install...

I added:
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary

to my /etc/apt/sources.list file and ran apt-get update

Then, I installed libapache2-mod-php5.0 first, php5.0 next, and mysql-php5.0 last.

then restarted apache2

...and I'm still getting 4.3.10-10ubuntu4.1 in my phpinfo page.

I'm an old NT Admin, so I even tried rebooting the box just in case, but no luck.  :-)

I'm fairly new to Linux, and Debian/Ubuntu especially, so I'm sure I've made a bonehead mistake, anybody know what it might be?

---

### Post by Adam (NZ) on 2005-10-01
[QUOTE=ergi1075]Hi, I must be missing something, can someone help?
Starting with a working Apache2/PHP 4 install...
I added:
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 hoary
to my /etc/apt/sources.list file and ran apt-get update
Then, I installed libapache2-mod-php5.0 first, php5.0 next, and mysql-php5.0 last.
then restarted apache2
...and I'm still getting 4.3.10-10ubuntu4.1 in my phpinfo page.
I'm an old NT Admin, so I even tried rebooting the box just in case, but no luck.  :-)
I'm fairly new to Linux, and Debian/Ubuntu especially, so I'm sure I've made a bonehead mistake, anybody know what it might be?[/QUOTE]

Hmmm - well, I have to admit that I've just realised my install was on a *clean* install of Ubuntu - with no previous Apache/PHP versions.

I'm not sure, but I think you're supposed to be able to run PHP4 and PHP5 *side by side* so may may need to Google around to see how to get into the v5 version.

If you're thinking of reinstalling from scratch, I'd wait a couple of weeks till 5.10 (Breezy Badger) comes out, as it has PHP5 built in.

---

### Post by ergi1075 on 2005-10-03
I figured it out!  I googled a lot, but didn't find this.  I actually stumbled across it myself.  Here's my solution if anyone needs it:

apache2.conf includes modules from

/etc/apache2/mods-enabled/

All of the files in that directory are just symlinks to modules that are located in this one:

/etc/apache2/mods-available/

I just deleted the php4 symlinks and added symlinks to the php5 modules (php5.0.conf and php5.0.load):

ln -s /etc/apache2/mods-available/php5.0.conf
ln -s /etc/apache2/mods-available/php5.0.load

restarted apache2, then php5 was up and running.

:)

---

### Post by tomasvilda on 2005-10-12
Sometimes I get apache segmentation fault when using dexter's php5 and mysqli extension.. Don't know how to get rid of this..

---

### Post by mgor on 2005-10-16
[QUOTE=ggnore]Hello.

I used your tutorial to install php5.
I also installed prado which is a framework.

The problem is that php5 seems to not be working correctly : i have a problem with sessions.

I m not sure, but i think that the php5 that is on the dexter repository is compiled without sessions management ...[/QUOTE]

have you installed php5(.0|.1)-session ?
if you have, make sure theres a symbolic link from /etc/php/conf.d/500session (something) to /etc/php/apache2/500session

---

### Post by humanbeing on 2006-01-04
as root i'm do the command **apt-get install mysql-php5.0**
  I get the following error
[I] Reading package list...Done
Building dependency tree...Done
E: Couldn't find package mysql-php5.0[/I]

I'm pretty new to linux.  I install hoary version with apache2 and PHP4 working.  I'm just trying to upgrade to PHP5

---

### Post by jordanka on 2006-11-07
Hallo.
Like the buddy above me (^) I'm a Ubuntu 5.04 user and I installed php4 and mysql4 from my Synaptic. I need to get php5 (mysql5) installed. The stuff I find online is quite confusing me so I'm asking for your help to tell me what to do or give me some (external) links or whatever you may consider useful.

Thank you, 
jordanka.

---

### Post by R960XT on 2007-03-02
hi, i want to ask a few question.
yesterday i downloaded the latest version of php which is** php-5.2.1.tar.bz2**
but when i tried to install it i got these message 

```
deddy@Linux:~/Desktop/php-5.2.1$ sudo ./configure
Password:
loading cache ./config.cache
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for icc... no
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking whether ln -s works... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for re2c... no
configure: warning: You will need re2c 0.9.11 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for bison... no
checking for byacc... no
checking for bison version... invalid
configure: warning: bison versions supported for regeneration of the Zend/PHP parsers: 1.28 1.35 1.75 1.875 2.0 2.1 2.2 2.3 (found: none).
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 3375: lex: command not found
configure: error: cannot find output from lex; giving up


```

i really don't know what's wrong please help me..
i have installed apache2 from source and i use ubuntu 6.06

---

### Post by Gerard Barberi on 2007-03-02
> **R960XT said:**
> 
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 3375: lex: command not found
configure: error: cannot find output from lex; giving up

[/code]

i really don't know what's wrong please help me..
i have installed apache2 from source and i use ubuntu 6.06

Try checking if flex is installed

sudo apt-get install flex

EDIT:  I think you might need bison too.

---

### Post by R960XT on 2007-03-02
i think it's not installed... :D
do i need to add the repository ??
please help me i'm newbie on linux 
```

deddy@Linux:~/Desktop/php-5.2.1$ sudo apt-get install flex
Password:
Reading package lists... Done
Building dependency tree... Done
Package flex is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flex has no installation candidate
deddy@Linux:~/Desktop/php-5.2.1$


```

btw what's bison ??

---

### Post by Gerard Barberi on 2007-03-02
Don't know what repos you have enabled.

You can find out by...

sudo gedit /etc/apt/sources.list

but, [this is flex]("http://packages.ubuntu.com/dapper/devel/flex") and [this is bison]("http://packages.ubuntu.com/dapper/devel/bison")

---

### Post by R960XT on 2007-03-03
wow, thanks man...
but i got another problem again :D

```


Configuring extensions
checking whether to enable LIBXML support... yes
checking libxml2 install dir... no
checking for xml2-config path...
configure: error: xml2-config not found. Please check your libxml2 installation.


```

but i've google around and found that i got to install libxml2dev again from source.
i'm downloadin it now.

---

### Post by Gerard Barberi on 2007-03-03
libxml2 is in the repos.

---

### Post by movil on 2007-04-13
I had some problems trying to install it in breezy, this is what I finally did:
* Added this packages:
> 
# PHP5.0 for Ubuntu breezy
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 breezy
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.0 breezy

then I did an apt-get update and : 
sudo apt-get install php5

Now I'm wondering if this can be installed in the 6.1 ( Edgy ) . Anyone did it ?

---

### Post by dmizer on 2007-04-13
edgy and dapper both have php5 in the ubuntu repos, and requires nothing more than:
```
sudo aptitude install php5
```

edgy has a "lamp" server install option that gives you apache, mysql, and php5 out of the box.

---

### Post by sapatos on 2008-03-04
hi. i have a problem.when i run my file [http://localhost/index.php](http://localhost/index.php) i'v got this message 

Not Found
The requested URL /index.php was not found on this server.

thank you.

---

