---
title: "SuperKaramba &quot;Fantastik&quot; problem... help!!"
date: 2006-11-28
forum: General Help
---

### Post by unlokia on 2006-11-28
Hi people!. I am using Edgy Eft (with kDE installed) and I am using "Fantastik" installed under 'superkaramba'.

I want to set my email details in the 'mails_pop3.pl' file, but HOW??

```
#!/usr/bin/perl
use Net::POP3;

my $ServerName = $ARGV[0];

# If your username contains a @ character you
# must replace it with \@
my $UserName = $ARGV[1];
my $Password = $ARGV[2];

my $pop3 = Net::POP3->new($ServerName);

if (!$pop3) {
	print "server unreachable";
}

my $Num_Messages = $pop3->login($UserName, $Password) + 0;

if ( $Num_Messages == 1 ){
   print $Num_Messages ." new mail\n";
}
elsif ( $Num_Messages > 1 ){
    print $Num_Messages ." new mail\n";
}
else{
    print "no new mail\n";
}

$pop3->quit();

```

Where in here do I edit, to put my details and servers...?

---

### Post by unlokia on 2006-11-29
Anyone?!!!!!!!!!!

---

### Post by kuja on 2006-11-29
You pass them in as arguments to the script. The first argument is the server name, second is the user name, third is the password

Example:

./mails_pop3.pl someserver my_email\@blah.com patheticpassword

---

### Post by unlokia on 2006-11-29
Hey would you mind elaborating on that a little bit, seeing as I am a total karamba n00b! :). Many thanks for your reply!

---

### Post by kuja on 2006-11-30
Hmm, looks like I missed the superkaramba part, but the idea is the same.

I downloaded fantastik3 off of kde-look and I'm pretty sure I've found where this stuff needs to go:

Open the file fantastik.theme, scroll down to a line that looks like this: > text x=55 y=178 sensor=program program="python2.4 ~/karamba/fantastik-3.0/progra
ms/pop3_ssl.py pop.gmail.com USER PASSWORD" line=1 color=0,0,0 fontsize=12 font=
"Tahoma" interval=18000

I do believe this is where you make the changes. Also, to make it work, tyou may want to change the location of the one file it mentions to something relative, it looks like this theme makes the bad assumption that this theme is in ~/karamba, which may not necessarily be true.

---

### Post by unlokia on 2006-11-30
Thanks for your response!. I find this whole theme flawed and confusing, therefore I am trashing it immediately. I wish the authors of scripts that need to be edited in order to work, would leave PROPER instructions on how to do so. Widgets should not be the realm of geeks - ordinary mortals want to use them also!.

Maybe I am wrong, but I could waste hours on this, when I could be using another (better) theme that is far more user friendly and efficient *and* easy to edit. I really do appreciate your help, nonetheless!!. :D

---

