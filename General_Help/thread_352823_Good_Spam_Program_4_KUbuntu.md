---
title: "Good Spam Program 4 K/Ubuntu"
date: 2007-02-03
forum: General Help
---

### Post by jrickmar on 2007-02-03
I came across a neat program called MailWasher that not only deletes messages and blacklists spammers, but also bounces the messages back to the sender saying that this isn't a legitimate address, so they stop spamming you.  But when I went to download it, I found that only Windows is supported, and that if you want a Linux or Mac version, you have to buy a premium version.  This, of coarse, just made my day. :( 

Is there some comprable program for Linux that is Free (like GNU)?  If so, I would love to know about it.

---

### Post by harley_frog on 2007-02-03
Well, this isn't exactly the same, but I use it and found it a great program: POPfile.  There is a  package available for Ubuntu.  It's a naive Bayesian filter/proxy server written in Perl.  You have to "train" it and maintain it through a web-based interface, but it correctly tags >98% of the email (YMMV).  Check it out at [http://popfile.sourceforge.net](http://popfile.sourceforge.net)

---

### Post by jrickmar on 2007-02-03
will it work in KMail? I installed it, but it wasn't recognized in the spam wizard.

---

### Post by harley_frog on 2007-02-04
It should.  You have to point Kmail to the POPFile proxy server.  This link should help: [http://popfile.sourceforge.net/wiki/howtos:kmailspamwizard](http://popfile.sourceforge.net/wiki/howtos:kmailspamwizard)

---

### Post by jrickmar on 2007-02-05
I saw that page when I was looking at POPFile already.  The only  problem is that that page covers v.1.71 when I use 1.9.6, so it was quite fuzzy.  Is there a tutorial that covers newer versions of KMail?  Right now I'm using SpamAssassin, Bogofilter, & DSpam.

---

### Post by harley_frog on 2007-02-05
Quick question: Are you downloading your e-mail using POP3 (like from Gmail) or is it going directly to your computer (as a mail server)?

---

### Post by jrickmar on 2007-02-06
I have an account at Runbox and have it set up using POP3.

---

### Post by harley_frog on 2007-02-07
Thanks for the info.  I don't use Kmail myself (I prefer Thunderbird), but I do have it installed and I hacked the code a bit, did some digging, and hopefully this will work.  Please note: I am running SimplyMEPIS 6.0 with the Ubuntu repositories and running Kmail v. 1.9.3.  If there are any differences between your system and mine, that I can't help. *shrug*

With that disclaimer out of the way, here is the relevant info about my system (be sure to check yours for similarities/differences):

Path to kmail.antispamrc: /etc/kde3/kmail.antispamrc

Path to POPFile settings: /usr/share/popfile/

Port settings from /etc/popfile/default: UIPORT=8080  POPPORT=8081

(If your port settings are different from the ones above, make note of them and make the appropriate change to the reclassify.pl code below. Step 6)

Contents of kmail.antispamrc:

```

[GENERAL]
tools=8

[SPAMTOOL #1]
...

```

1.  Make a backup copy of kmail.antispamrc

```
sudo cp /etc/kde3/kmail.antispamrc /etc/kde3/kmail.antispamrc.backup
```

WARNING! Failure to make backup copy could result in temporary loss of sanity. ;)

2.  As root (using sudo), open up /etc/kde3/kmail.antispamrc in your favorite text editor (Kate is a good choice; I prefer emacs)

3. Change the tools to one number greater (in my case tools=9).

4. Add the following to end of your kmail.antispamrc making sure that the Spamtool number equals the tools number at the top of the file (see step 3).
```

[Spamtool #9]
Ident=popfile
Version=1
VisibleName=POPFile
Executable=/bin/true
URL=http://popfile.sourceforge.net
PipeFilterName=POPFile Check
PipCmdDetect=/bin/true
ExecCmdSpam=/usr/share/popfile/reclassify.pl spam
ExecCmdHam=/usr/share/popfile/reclassify.pl normal
DetectionHeader=X-Text-Classification
DetectionPattern=spam
UseRegExp=0
SupportsBayes=1

```

5. Save your modified version of kmail.antispamrc.

6. In your text editor, open a new file and copy the following code and paste into your text editor.
```
#!/usr/bin/perl 
use strict; 
use XMLRPC::Lite; 
 
# This XMLRPC client reclassifies a message 
# REQUIRES X-POPFile-Link be enabled for all messages processed 
# Usage: 
# ./xmlrpc-reclassify.pl bucket < message 
 
my $bucket; 
die ( "You must specify a bucket!" ) unless ( $bucket = $ARGV[0] ); 
 
my $message; 
 
# act like a pipe, reading from STDIN 
while (<STDIN>) { 
if ($_ =~ /^X-POPFile-Link: .*?\?view=([0-9]+)/) { 
$message = $1; 
last; 
} 
} 
 
die ( "No X-POPFile-Link header found") unless ( defined( $message ) ); 
 
print STDERR "Reclassifying message $message to $bucket\n"; 
 
# our XMLRPC proxy 
my $xmlrpc = XMLRPC::Lite ->proxy('http://localhost:8081/RPC2'); 
 
# say hello and get a session key 
my $sk = $xmlrpc-> call('POPFile/API.get_session_key','admin','') 
-> result; 
 
die ( "Unable to obtain a session with POPFile. \ 
Please verify that POPFile is running and\ 
your username and password are correct. $sk" ) if ($sk eq '' || !defined($sk) ); 
 
# this does the work 
my $result = $xmlrpc-> call('POPFile/API.reclassify',$sk , $message, $bucket ) 
-> result; 
 
# release, release 
$xmlrpc-> call('POPFile/API.release_session_key',$sk); 
 
die( "An error occured while reclassifying: $result" ) unless ( $result eq '0' ); 
 
# exit 
exit(0);

```

Save this file as reclassify.pl and save it to /usr/share/popfile/.

Original post for the above code is from here: [http://sourceforge.net/forum/forum.php?thread_id=1215502&forum_id=230652](http://sourceforge.net/forum/forum.php?thread_id=1215502&forum_id=230652)

7.  Open up Konsole and issue the following command:
```

sudo chmod a+x /usr/share/popfile/reclassify.pl

```

8.  Follow the directions from [http://popfile.sourceforge.net/wiki/howtos:kmailspamwizard](http://popfile.sourceforge.net/wiki/howtos:kmailspamwizard) under the heading: Using the Wizard.  (Your version of Kmail will look different from the screenshots, but not enough to cause too much confusion, I hope. ;) )

I hope this works.  As I said, I use Thunderbird and the setup is different.  I tried doing it the configuration in Kmail that I use for Thunderbird, but Kmail wouldn't allow me to do it. :(  Again, your milage may vary.

---

### Post by jrickmar on 2007-02-09
Got it installed and seems to work.  Thanks.

---

### Post by dcstar on 2007-02-10
> **jrickmar said:**
> I came across a neat program called MailWasher that not only deletes messages and blacklists spammers, **but also bounces the messages back to the sender saying that this isn't a legitimate address, so they stop spamming you**. 
.......

The harsh facts are that a lot of Spam uses forged "Reply To" addresses, so any replies you then send may well be Spam to innocent recipients.

As well, a lot of Spam has no idea if your particular e-mail address is actually valid, so by replying you are basically letting the Spammers know that your address is valid, and that they can now send even more Spam to you with the confidence that it is being received.

Do the world, and yourself, a favour and never, ever bounce or reply in any way to Spam.

---

