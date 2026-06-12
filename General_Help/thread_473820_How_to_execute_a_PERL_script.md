---
title: "How to execute a PERL script?"
date: 2007-06-14
forum: General Help
---

### Post by chunchengch on 2007-06-14
I was asked to execute a PERL script to fix compatible problem? should anyone tell me how to do?
thanks a lot!

---

### Post by mannheim on 2007-06-14
If you are in gnome, and don't want to use the command-line, do this. (I assume the script is saved in a file, and that the text in the file begins with something like "#!/bin/perl" or similar:
[LIST=1]
[*]Right-click on the file, and select "Properties"
[*]Select the "Permissions" tab.
[*]Check the box that says "Allow executing file as a program"
[*]Close the Properties dialog box
[*]To run the perl script, double-click on the file
[*]If a dialog asks for confirmation, click the button that says "Run"
[/LIST]

Alternatively, open gnome-terminal, go to the directory in which the file is located, and then enter "perl myfile", replacing "myfile" with the name of the file.

---

### Post by stchman on 2007-06-14
> **chunchengch said:**
> I was asked to execute a PERL script to fix compatible problem? should anyone tell me how to do?
thanks a lot!

Yes, make sure you give the file 755 permissions and it has to have 

#!/usr/bin/perl 

as the first line of the script.  This will tell the shell to use the PERL interpreter.

---

### Post by gerscht on 2007-06-14
you can also run
```

perl /path/to/script

```
then the script doesn't need the first line and doesn't need to be executable

---

### Post by chunchengch on 2007-06-14
Thanks all,

I don't know how to save the script to a file, here is the script :

[B]#!/usr/bin/perl
die "File $ARGV[0] doesn't exist" unless -f $ARGV[0];
use MP3::Mplib;
my $mp3 = MP3::Mplib->new($ARGV[0]);
my $v2tag = $mp3->get_v2tag;
print "Error writing tags of $ARGV[0]\n" unless $mp3->set_v2tag($v2tag,&UTF8);[/B]

---

### Post by gerscht on 2007-06-15
Just open a text editor (like gedit), paste it in and save it as 'name.pl' (name is up to you and the pl extension is not needed, but most people add the extension to know what file is)  :D
for example:
```

gedit ~/mp3tags.pl &

```
Paste the code from your post, press save

make it executable
```

chmod +x ~/mp3tags.pl

```

Run it
```

~/mp3tags.pl /path/to/my/mp3file.mp3

```

---

### Post by chunchengch on 2007-06-16
Hey thanks a lot, I am such a Linux newbie that need helps all the time.;)

---

