---
title: "[SOLVED] I need a script..."
date: 2007-08-12
forum: General Help
---

### Post by jackmc on 2007-08-12
ok, heres what I need to do.

My dad has a text file which is a long list of strings of text to be imported into a program. I need to add inverted commas (") at the beginning and end of every line in the file. How would I go about doing this?

Thanks a lot :)

---

### Post by lloyd_b on 2007-08-12
A fast and simple way: use the "vi" editor and some search/replace commands.  In a terminal window,  "cd" to the appropriate directory (if needed), then:
[SIZE="4"]```
vi filename
:s/\&/"/
:s/\n/"\r/
:wq
```[/SIZE]

One comment - you may need to add the final " at the end of the last line of the file...

Lloyd B.

---

### Post by jackmc on 2007-08-12
ok, that did the first item, but not the rest. When I open the file in vi, each line has ^M at the end - is that normal?

---

### Post by yabbadabbadont on 2007-08-12
That just means that the file was saved in DOS/Windows mode.

---

### Post by lloyd_b on 2007-08-12
> **jackmc said:**
> ok, that did the first item, but not the rest. When I open the file in vi, each line has ^M at the end - is that normal?

Just to clarify: "did the first item" means what?  Just the first line?  Or prepended the " to all lines?

As to the ^M's at the end of the lines - you're looking at an MS-DOS file (which ends the lines with CR + LF) as opposed to a Unix file (which ends the line with a "newline" character).  Ideally, you should use "dos2unix" to convert it into a Unix file, then use "unix2dos" to convert it back (if you need to move it back to a Windows machine).  However,try this command:
[SIZE="4"]```
:s/\r/"\r/
```[/SIZE]
and see if that handles the "end of line" addition...

Could you post a sample of what you're trying to convert?  That would make it a little easier to see what's going on...

Lloyd B.

---

### Post by jackmc on 2007-08-13
I thought I had replied to this thread, but apparantly not.

Attached is the complete file (should ne in unix "mode" now)

> 
Just to clarify: "did the first item" means what? Just the first line? Or prepended the " to all lines?


I meant that the first line of the file had inverted commas at both the beginning and the end, but none of the other files did.

---

### Post by HermanAB on 2007-08-13
A combination of 'find' and 'sed' can do it automatically in a single line:

find ./ -type f -exec sed -i 's/find-text/replace-text/' {} \;

Search with Google for 'bash find sed' and you should get a bazillion guides.

'Hope that helps!

Herman

---

### Post by jackmc on 2007-08-13
> **HermanAB said:**
> A combination of 'find' and 'sed' can do it automatically in a single line:

find ./ -type f -exec sed -i 's/find-text/replace-text/' {} \;

Search with Google for 'bash find sed' and you should get a bazillion guides.

'Hope that helps!

Herman

I just had a quick look at this, the problem is that there is no constant character to "find" on each line and then replace - unless I'm doing it wrong..

---

### Post by bjarneh on 2007-08-13
small perlscript to add " at the beginning and end of each line of a file

---------------------------------------------

#!/usr/bin/perl

use strict;

die "usage: myScript some_file_name" unless $#ARGV > -1;

my $filename = shift;

open FH, "<$filename";

while(<FH>){
    if(not $_ =~ /^\s$/){
        $_ =~ s/\n//g;
        print "\"$_\"\n";
    }else{
        print "$_";
    }
}

close(FH);

---

### Post by lloyd_b on 2007-08-13
> **jackmc said:**
> I thought I had replied to this thread, but apparantly not.

Attached is the complete file (should ne in unix "mode" now)



I meant that the first line of the file had inverted commas at both the beginning and the end, but none of the other files did.

Ok - the fact it only affected the first line was my fault - I forgot something in the commands...
[SIZE="4"]```
vi file.txt
:1,$s/\&/"/
:1,$s/\n/"\r/
:wq
```[/SIZE]
does the trick.  (the "1,$" business tells it to affect all lines; the commands I originally gave you only affect the current line.  Oops).

Lloyd B.

---

### Post by capink on 2007-08-14
Try this:

```
sed 's/\(.*\)/"\1"/' /path/to/the/file.txt
```

this command will only display the result on the terminal, it will not change the contents of the file. If it does what you want repeat the command with the -i option:

```
sed -i 's/\(.*\)/"\1"/' file.txt
```

---

### Post by jackmc on 2007-08-14
> **capink said:**
> Try this:

```
sed 's/\(.*\)/"\1"/' /path/to/the/file.txt
```

this command will only display the result on the terminal, it will not change the contents of the file. If it does what you want repeat the command with the -i option:

```
sed -i 's/\(.*\)/"\1"/' file.txt
```

perfect, thanks a lot :)

---

