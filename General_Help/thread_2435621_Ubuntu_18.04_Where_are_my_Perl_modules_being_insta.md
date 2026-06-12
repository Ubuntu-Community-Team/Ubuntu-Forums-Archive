---
title: "Ubuntu 18.04: Where are my Perl modules being installed?"
date: 2020-01-23
forum: General Help
---

### Post by bulrush2 on 2020-01-23
We have a new installation of Perl 5.26 on a new machine Ubuntu v18.04. It looks like our IT department created the virtual machine for Ubuntu like this: 


[LIST=1]
[*]Clone our old VM with Ubuntu 14.04. 
[*]Copy my home dir to the new machine. 
[/LIST]


It's been 5+ years since I configured this, so I'm a bit rusty with this part, and I'm installing all the modules my Perl programs need on the new Ubuntu. I'm trying to list the non-core modules I have installed but I can't seem to even find the directory they are going to. All modules are installed with cpanm. 

1. In which dir are my custom non-core modules being installed via cpanm? 

2. How do I list the non-core modules and their versions? 

I've spent about 2 hours researching this yesterday and today and have not found an answer. This command used to work to list custom modules for Perl but no longer works on Ubuntu 18.04: 
```
perl -MFile::Find=find -MFile::Spec::Functions -Tlw -e 'find {wanted => sub {print canonpath $_ if /\.pm\z/}, no_chdir => 1}, @INC' >> $tempfile
```

because I get an error 
```
Can't stat /usr/loca/lib/site_perl: No such file or directory
```, because that dir doesn't exist on the new system.

EDIT1: 

It might be my PERL5LIB is wrong, but it's not set in ~/.bashrc. However I wrote a Perl program to show the contents of @INC and the wrong dir, /usr/local/lib/site_perl, is in @INC and I'm trying to figure out how to get that dir out of @INC. 

The contents of @INC are in this order: 
```

/etc/perl
/usr/local/lib/x86_64-linux-gnu/perl/5.26.1
/usr/local/share/perl/5.26.1
/usr/lib/x86_64-linux-gnu/perl5/5.26
/usr/share/perl5
/usr/lib/x86_64-linux-gnu/perl/5.26
/usr/share/perl/5.26
[COLOR=#ff0000]/usr/local/lib/site_perl[/COLOR]
/usr/lib/x86_64-linux-gnu/perl-base

```

And I was able to find my modules under /usr/local/share/perl/5.26.1, so my problem seems to be I need to add /usr/local/share/perl/5.26.1 to my @INC variable. 

EDIT2:

Sorry for the length of the post but I wanted people to see what steps I'm doing. 

I just created the problematic dir /usr/local/lib/site_perl. Now my code to list modules above executes but shows no modules installed. 
```
perl -MFile::Find=find -MFile::Spec::Functions -Tlw -e 'find  {wanted => sub {print canonpath $_ if /\.pm\z/}, no_chdir => 1},  @INC' >> $tempfile
```

I run the command from a shell script and when I check the shell exit status it's 0. Here's the whole 'perlmodules' script I use in bash: 
```

# Jan 22, 2020. List all perl modules on system.
# Jan 2020: Does not work, path not found for 
echo " "
#echo "This does not work yet."
#exit 1

yymmdd=`date +%F`
tempfile=temp.txt
myhome=/home/chuck/bin
outfile=$myhome/perlmod-$yymmdd.txt
mydate=`date`
echo "Finding modules..."
echo "00 File Created on $mydate" > $tempfile
echo "Perl version `perl -v`" >> $tempfile
perl -MFile::Find=find -MFile::Spec::Functions -Tlw -e 'find {wanted => sub {print canonpath $_ if /\.pm\z/}, no_chdir => 1}, @INC' >> $tempfile

echo Status is: $?
if [ $? ]; then
    exit 1
fi
sort temp.txt > $outfile

echo "See $outfile"
echo " "

```

So the question remains, **how do I list the custom modules I have installed for Perl**? The code above stops immediately when it finds an invalid directory, and now it lists no modules at all.



Thank you!

---

