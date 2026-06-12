---
title: "nzbperl"
date: 2005-07-30
forum: General Help
---

### Post by i30i3i3y on 2005-07-30
Hi all,

I'm trying to get nzbperl working but i get this error message and I dont know what to do about it.

Can't locate XML/DOM.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./nzbperl.pl line 39.
BEGIN failed--compilation aborted at ./nzbperl.pl line 39.

I've run other perl scripts fine but whats up with this one?

Any help appreciated.

---

### Post by amohanty on 2005-07-30
It cannot find the XML::DOM packages in perl

Try (I dont remember the syntax offhand so this might be off) at the cmd line:
>> perl -MCPAN -e 'install XML::DOM'

and follow instructions.

AM

---

### Post by i30i3i3y on 2005-07-31
Thanks for the response. But it doesn't work :(

The terminal just sits there doing nothing till i break. Is there an apt-get or something I can do?

---

### Post by amohanty on 2005-07-31
Wait so you cannot run the :
perl -MCPAN command at all?

AM

---

### Post by i30i3i3y on 2005-08-01
well when i run it the cursor in the terminal goes to the next line and sits there doing nothing.

It doesnt spew out an error message, so i dont know if its doing something or just sitting idly. Is it supposed to take a really long time?

---

### Post by amohanty on 2005-08-01
ok try this:

>> perl -MCPAN -e shell

that will fire up the CPAN shell. If you have never used it before it will prompt you for several things to set it up or you could just answer _no_ to the first question and it will use defaults.
you will get to the cpan prompt
then at the prompt (cpan> is the prompt)

cpan> install XML::DOM

HTH
AM

Edit: Damn the smilies... its:
cpan> install XML:: DOM
without the space between : and D

---

### Post by i30i3i3y on 2005-08-02
ok, that was interesting :P. Spewing out text like nobody's business.

Now I have a new error,

root@ubuntu:/home/bobby/perl # ./nzbperl.pl
Can't locate Term/ReadKey.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./nzbperl.pl line 42.
BEGIN failed--compilation aborted at ./nzbperl.pl line 42.

Thanks for the help so far. I seem to have bitten off more than I can chew with this one. Other perl scripts ran so easily.

---

### Post by amohanty on 2005-08-02
run perl -MCPAN as root, ie sudo it. I have a root setup so I dont use sudo much, but try the following:

>> sudo perl -MCPAN -e shell

AM

Edit: Also you might need to install the appropirate Term modules, although it should automatically do it for you.

---

### Post by i30i3i3y on 2005-08-02
I have been runing it as root. Everything i've done so far is as root. I rarely use sudo, I just open up a root terminal.

When I said 'spewing out tex' tI didn't mean errors. It was doing stuff and installed everything ok (I said no to the first option). I'm able to open up the CPAN prompt. But after doing all that when I try to run nzbperl I get the error message above. maybe theres some other dependency I've yet to fill?

---

### Post by Dustin Wyatt on 2005-08-09
[QUOTE=i30i3i3y]I have been runing it as root. Everything i've done so far is as root. I rarely use sudo, I just open up a root terminal.

When I said 'spewing out tex' tI didn't mean errors. It was doing stuff and installed everything ok (I said no to the first option). I'm able to open up the CPAN prompt. But after doing all that when I try to run nzbperl I get the error message above. maybe theres some other dependency I've yet to fill?[/QUOTE]
 Was wondering if you were able to get this working.  I'm unable to install XML:DOM.

It spends forever doing a bunch of stuff but then compiling fails when I do this.

perl -MCPAN -e "install XML::DOM"

As per the nzbperl homepage ( [http://noisybox.net/computers/nzbperl/](http://noisybox.net/computers/nzbperl/) ), I was able to install IO::Socket::INET and File::Basename but when I got to XML::DOM, no luck.  :(

---

### Post by amohanty on 2005-08-09
> Can't locate Term/ReadKey.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./nzbperl.pl line 42.
BEGIN failed--compilation aborted at ./nzbperl.pl line 42. 

Just like last time you need to install Term::ReadKey module.

whenever you get something like: Can't locate ABC/xyz.pm you need to install the module ABC::xyz module. YOu can locate those atr cpan.org

HTH
AM

---

### Post by i30i3i3y on 2005-08-14
I've found a neater solution. Rather than mess around with perl just install klibido. Brilliant news reader, graphical as well. Installed it all on my own   :-P 

Need to install a bunch of kde libraries if you're using gnome. It's quite tricky under ubuntu (the standard debian package doesn't work) but follow the instructions at [http://klibido.sourceforge.net/#_download](http://klibido.sourceforge.net/#_download) and you should be fine.

---

### Post by action09 on 2005-12-09
1)    apt-get install libxml-dom-perl libterm-readkey-perl uudeview

will solve your error messages !




2) download nzbperl from the website  
and download too this:
wget [http://noisybox.net/computers/nzbperl/nzbperlrc.sample](http://noisybox.net/computers/nzbperl/nzbperlrc.sample) -O  ~/.nzbperlrc

3) edit  the ~/.nzbperlrc   to add e.g. user/pass of your news server...


4) enjoy !

---

### Post by transactionlogfiller on 2006-03-05
Thanks, action09.

I just did a fresh install and couldn't get nzbperl working. It had recently become one of my favourite applications, so good thing I found your post.

---

### Post by utw-mephisto on 2006-11-05
> **action09 said:**
> 1)    apt-get install libxml-dom-perl libterm-readkey-perl uudeview

will solve your error messages !




2) download nzbperl from the website  
and download too this:
wget [http://noisybox.net/computers/nzbperl/nzbperlrc.sample](http://noisybox.net/computers/nzbperl/nzbperlrc.sample) -O  ~/.nzbperlrc

3) edit  the ~/.nzbperlrc   to add e.g. user/pass of your news server...


4) enjoy !

I know its an old post, but found it on google / vbulletin archive when I was looking for a solution .. This saves the day :) Thanks a lot

---

### Post by Craftkiller on 2008-01-21
are you running that command as root and/or sudo? i used to end with an error if i didnt put sudo infront

---

