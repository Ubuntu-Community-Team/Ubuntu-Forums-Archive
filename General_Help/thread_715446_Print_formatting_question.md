---
title: "Print formatting question"
date: 2008-03-04
forum: General Help
---

### Post by geofffox on 2008-03-04
I am a meteorologist.  As part of my day, I look at this [forecast guidance]("http://www.nws.noaa.gov/cgi-bin/lamp/getlav.pl?sta=KBDR&sta=KDXR&sta=KGON&sta=KBDL&sta=KHFD&sta=KMMK&sta=KHVN&sta=KOXC&sta=KIJD").

Usually, I print it by bringing it into Firefox.  I'd like to run a cron and have it printed and waiting for me.  However, when I do, it is much larger and spreads off the printed page.

Is there any way I can use a shell script and have it printed and remain the size Firefox renders it?

Thanks,
Geoff Fox

---

### Post by kool_kat_os on 2008-03-04
what cron do you use?

---

### Post by geofffox on 2008-03-04
Not sure what you're asking.  I just write the cron using vi (crontab -e).

---

### Post by ghostdog74 on 2008-03-04
> **geofffox said:**
> I am a meteorologist.  As part of my day, I look at this [forecast guidance]("http://www.nws.noaa.gov/cgi-bin/lamp/getlav.pl?sta=KBDR&sta=KDXR&sta=KGON&sta=KBDL&sta=KHFD&sta=KMMK&sta=KHVN&sta=KOXC&sta=KIJD").

Usually, I print it by bringing it into Firefox.  I'd like to run a cron and have it printed and waiting for me.  However, when I do, it is much larger and spreads off the printed page.

Is there any way I can use a shell script and have it printed and remain the size Firefox renders it?

Thanks,
Geoff Fox

you can use wget to get the page and save locally.
you can use lp to print to printers in *nix.
check the man page for wget and lp for more information

---

### Post by geofffox on 2008-03-04
I tried that, but lost the formatting.

Printing it is no problem.  Printing it in a compact form so it stays n a single page is.

---

### Post by unutbu on 2008-03-04
geofffox, can you explain what script/commands you used to download and print the page? I'm curious why it spreads off the page.

Do you have perl, wget, and a2ps on your system? If so here is a solution:

Save this to a file named something like 'get_forecast' and configure cron to run it daily:

```

#!/usr/bin/perl

my $cmd='wget "http://www.nws.noaa.gov/cgi-bin/lamp/getlav.pl?sta=KBDR&sta=KDXR&sta=KGON&sta=KBDL&sta=KHFD&sta=KMMK&sta=KHVN&sta=KOXC&sta=KIJD" -O tmp.html';
system($cmd);

open(FILE,"<","tmp.html") || die "Can't open tmp.html";
open(TXT,">","tmp.txt") || die "Can't open tmp.txt";
my $count=0;
while (<FILE>) {
    next if /^\</;
    last if /^Go back/;
    if (/^\s*$/) {
	$count++;
	if ($count==1) {
	    next;
	} elsif ($count==3) {
	    $count=0;
	}
    }
    print TXT;
}
close(TXT);
close(FILE);

$cmd="a2ps --no-header --columns=1 --portrait --chars-per-line=81 --lines-per-page=65 -o tmp.ps tmp.txt";
system($cmd);
$cmd="lpr tmp.ps";
system($cmd);

```


The perl script above will create 3 files: tmp.html, tmp.txt and tmp.ps. Be sure that does not conflict with any files with the same names that you don't want overwritten.

I'm sure there is a way to do this using a sh script, but I unfortunately do not know sh well... it's just so easy to do things with perl I never learned sh.

---

### Post by unutbu on 2008-03-04
If you don't have perl and don't want to install it on your system, and if you don't mind printing some html code before and after your data, all you really need is a2ps. 

You can rip that command out of the perl script and just stick it in an sh script. This will allow you to avoid having to install perl if it is not already on your system.

---

### Post by geofffox on 2008-03-04
I will try this tomorrow.  I do have perl in this system.  And, I do thank all of you for your assistance.

Geoff

---

### Post by geofffox on 2008-03-04
oops - lpr: Error - unable to access "tmp.ps" - No such file or directory

So, close, but no cigar - yet.

---

### Post by unutbu on 2008-03-04
maybe "change directory" at the beginning of the script so you know for sure where the tmp.ps file will be created:

Make a tmp directory under your home dir. Then edit the script:

```

#!/usr/bin/perl
chdir("$ENV{HOME}/tmp");
...

```

Then the file will be in ~/tmp/tmp.ps.

---

### Post by geofffox on 2008-03-05
I am home now.  Will try tomorrow afternoon and report back.

---

### Post by geofffox on 2008-03-05
Problem solved.  The original script is totally correct.

I had assumed a2ps was installed.  It was not.

For other 'newbies' following this thread later, I opened a terminal an entered 'which a2ps'

That command should give the path to the program.  It gave me no result, which is how I knew it wasn't installed.

I opened Synaptic and installed it all in about 20 seconds.

Thanks again to all who have helped.

---

