---
title: "Bash sed special characters and variable"
date: 2022-11-24
forum: General Help
---

### Post by moondragon2009 on 2022-11-24
Hi, I would like to replace with sed
```
''
```
with
```
'Z:$var'
```
$var = \test\test.txt
I tried with
```
sed -i -e "s,\'\',\'Z:$var\',g" file.txt


```
but here it adds me after each line instead of replacing.
I'm no expert, and I'm trying to make a [script for Lutris]("https://github.com/lutris/lutris/issues/4602"), can anyone help me?

---

### Post by TheFu on 2022-11-24
I'd use perl.
```

#!/usr/bin/env perl

while (<>){
   my $var="foo";
   s#''#'Z$var'#o;
   print ;
}

```
Test with input file:
```

1 
2 
3 ''
4 ' you '
5 " too" 
6 
7 

```
Results are:
```

$ ./t.pl t
1 
2 
3 'Zfoo'
4 ' you '
5 " too" 
6 
7 

```
Took me more time to post this tested stuff than it took to create. I was actually shocked when it worked the first time.

If I need to make the same change on 5+ computers, I'd use ansible. It has a built-in regex change engine to alter configuration files and would only change a file if needed, not blindly like other tools, including sed/perl.

---

### Post by MAFoElffen on 2022-11-24
Try this, using escape characters for the regular expression:
```

sed -i -e 's/\'\'Z:\$var\'/g' file.txt

```
I corrected your format of the  expression...

If I am scripting something like that on hard files, I create a temporary file and copy it over, then delete the temp file... If you do 'sed' in-place, it does the same under the covers. So doing it manually does the same. Both ways use the same cpu and memory. Manually just gives you a change to see and debug the process, to see what is going on.

I admit, I always leaned towards in-place replacements... Until a member of my team challenged me on that. At first, I resisted. The argument he presented won me over. It makes sense for maintainability and debugging.

---

### Post by moondragon2009 on 2022-11-24
Thank you for your reply,**[COLOR=#000000] [/COLOR]**[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685") 	  						 The problem is that the rest of the script is in bash and it becomes laborious to call another external script in Perl.
I was thinking of using sed because I only have one call when I start the programme, I summarise:
click on file > bash script starts > program starts under wine with argument created by the script

---

### Post by moondragon2009 on 2022-11-24
Thank you for your reply, [**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547")
yes I create the modification on a temporary file and then send it to another file, moreover when the wine programme is closed, the original file is restored, I just need it to create the argument to pass to the programme when it starts, i.e. a certain file on which I will make two clicks to open it.
I tried your sed line of code on the terminal but it opens a line with '>' (looks like I should write something in it) and does not change anything

---

### Post by TheFu on 2022-11-24
> **moondragon2009 said:**
> Thank you for your reply,**[COLOR=#000000] [/COLOR]**[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685") 	  						 The problem is that the rest of the script is in bash and it becomes laborious to call another external script in Perl.
I was thinking of using sed because I only have one call when I start the programme, I summarise:
click on file > bash script starts > program starts under wine with argument created by the script

There's little difference between calling sed and calling perl, but whatever.  WINE is your real problem, not a native tool.  Any perl script can be re-written as a 1-line script.  I didn't show that to keep it very simple, but if the sed solution works for you - I'd use that myself.  awk would be another method with more control than sed.  Long ago, I was doing some processing that used a Windows-only tool for 1 aspect, but most of the work was handled on Linux.  My solution was to load strawberry perl onto MS-Windows and have it 
* copy the input file(s) to Windows in the middle of the night (30min to move everything), 
* Run the Windows-only tool spawn from Perl to do some batch processing (2+hrs to run),
* Manually validate the results from the batch (30sec per file), 
* Copy the files and newly created data back to Linux, which was watching for them to appear in a special directory, 
* Run the next phase of the processing, massively reducing the input files, 
* Run the next phase of the processing, converting the input files to a different, more efficient format.  Sizes for the original files was around 10G. The final finished files would be 1G-1.5G.  Most importantly, I'd spend 1-2 minutes on this, not 3 hrs, if I were doing it manually and waiting.

> I tried your sed line of code on the terminal but it opens a line with '>' (looks like I should write something in it) and does not change anything 
That means the quoting characters are unbalanced.  That is common with any search and replace tool ... which is why perl supports using any delimiter as desired.  I chose a '#' character, but people commonly use a '/' or a '|' instead.  Really depends on the input data and the regex.  Flexibility is why perl is still keeping the internet working today and most people don't realize that to be true.  It is still the glue that make all our networks stick together.  Slowly, python is taking over, but only when something with 20+ yrs of proven use fails, which isn't very often.

---

### Post by MAFoElffen on 2022-11-24
I debugged and tested it. Changed to:
```
sed -i -e "s/\'\'/\'Z:$var\'/g" file.txt
```
I took out the escape on $, since you are passing a variable to it, instead of the literal text... and I tested it passing a variable in the expression.

---

### Post by moondragon2009 on 2022-11-25
> **TheFu said:**
> There's little difference between calling sed and calling perl, but whatever.  WINE is your real problem, not a native tool.  Any perl script can be re-written as a 1-line script.  I didn't show that to keep it very simple, but if the sed solution works for you - I'd use that myself.  awk would be another method with more control than sed.  Long ago, I was doing some processing that used a Windows-only tool for 1 aspect, but most of the work was handled on Linux.  My solution was to load strawberry perl onto MS-Windows and have it 
* copy the input file(s) to Windows in the middle of the night (30min to move everything), 
* Run the Windows-only tool spawn from Perl to do some batch processing (2+hrs to run),
* Manually validate the results from the batch (30sec per file), 
* Copy the files and newly created data back to Linux, which was watching for them to appear in a special directory, 
* Run the next phase of the processing, massively reducing the input files, 
* Run the next phase of the processing, converting the input files to a different, more efficient format.  Sizes for the original files was around 10G. The final finished files would be 1G-1.5G.  Most importantly, I'd spend 1-2 minutes on this, not 3 hrs, if I were doing it manually and waiting.


That means the quoting characters are unbalanced.  That is common with any search and replace tool ... which is why perl supports using any delimiter as desired.  I chose a '#' character, but people commonly use a '/' or a '|' instead.  Really depends on the input data and the regex.  Flexibility is why perl is still keeping the internet working today and most people don't realize that to be true.  It is still the glue that make all our networks stick together.  Slowly, python is taking over, but only when something with 20+ yrs of proven use fails, which isn't very often.

I think I understand, the main problem lies in Lutris running wine, as it does not integrate external file management such as Playonlinux or Crossover.
I also tried your script in perl, but you have problems with the variable if it contains \ , I need my variable to be a file path, the Z: is the letters that wine assigns to the Ubuntu hardisk.
Also I don't know perl, so no file is currently written but only printed.

---

### Post by moondragon2009 on 2022-11-25
> **MAFoElffen said:**
> I debugged and tested it. Changed to:
```
sed -i -e "s/\'\'/\'Z:$var\'/g" file.txt
```
I took out the escape on $, since you are passing a variable to it, instead of the literal text... and I tested it passing a variable in the expression.
I tried this but it adds after '', 'Z:' 
I will put you all the script I have written so far.
with this in mind:
(a) PROG = program installed in Lutris.
b) EXT = extension of the files that are to be opened with the PROG program.
c) 4 = Lutris bottle code where PROG is installed.
d) 12345 = PROG identification code

I have created in
```
$HOME/.local/share/applications/
```
a file called
```
wine-extension-EXT.desktop
```
with inside
```
[Desktop Entry]
Type=Application
Name=PROG
MimeType=application/EXT;
Exec=$HOME/EXT-script.sh
NoDisplay=true
StartupNotify=true
Icon=lutris_PROG
```
I assigned opening file.EXT to that program *.desktop

Well now the script "EXT-script.sh" that should solve my problem is this: 
```
#!/bin/sh
var=`cat $HOME/.EXTtmp.txt`
echo "$@" >> $HOME/.EXTtmp.txt
sed -i -e 's:/*/:\\:g' $HOME/.EXTtmp.txt
cp $HOME/.config/lutris/games/PROG-12345.yml $HOME/.PROG-12345.yml
sed -i -e "s/\'\'/\'Z:$var\'/g" $HOME/.config/lutris/games/PROG-12345.yml
Exec=env LUTRIS_SKIP_INIT=1 lutris lutris:rungameid/4
rm $HOME/.EXTtmp.txt
cp $HOME/.PROG-12345.yml $HOME/.config/lutris/games/PROG-12345.yml
rm $HOME/.PROG-12345.yml
exit

```
The problem is the second sed that doesn't work as it should, that's why I asked for help

---

### Post by TheFu on 2022-11-25
```
var=`cat $HOME/.EXTtmp.txt`
```
seems wrong.  I'd make it have a var="xyz" inside it and do
```
source $HOME/.EXTtmp.txt
```
instead.  This way, we don't have to worry about end-of-line or end-of-file characters.

BTW, using `run something` has some issues.  Best to make those $(run something) and use bash.  I'm not even certain Bourne shell supports the source built-in. All Linux should have bash, so that would be safe and for scripting it handles things a bit nicer.

Do .desktop files allow using environment variables in paths?  IDK.  I don't really use .desktop files at all ... or menus.

Not that it matters, but the perl script as written supports inputs from either stdin or a specified file globbing and writes all outputs to stdout. This follows the Unix philosophy and means that if we want to pipe the output to another program, we can.  Or we can redirect the output to a file.  All standard stuff.   But for your needs, I'd stick with bash too or just replace the entire .desktop wackiness and .sh with a perl script.  

You do know that you don't need .desktop files at all, right?  There are lots of ways to have bash/sh/perl/python run external programs directly and either let the console output go to the console or capture it by any of those tools for other purposes.  Bash and Bourne shell can have little menu systems either pre-created or generated on the fly.  I use both. whiptail is an easy TUI menu and the old readarray, echo, and select method works.  There are competitors to whiptail, but they code very similarly, IME. I liked the resulting menu that whiptail generates more.  Plus, it lets us make the menu with accel keys. The readarray-select only provides numbers to select. For many problems, that's fine. Not so much for program controls.  Sigh.

---

### Post by TheFu on 2022-11-25
I Put Z: into the substitution:

```
$ ./t.pl t
1 
2 
3 'Z:foo'
4 ' you '
5 " too" 
6  \what's the issue?
7  Z:/path/to/file 
8  Z:\path\to\file 

```
BTW, Windows supports using '/' as a directory separator, just like in Unix.  For cross-platform coding, this has been the situation since the beginning. Including cmd.exe.
Z:/path/to/file will work fine.

Call me confused.  If the argument is being used for the substitution, perhaps your shell is altering it before handing it over to the script?   Use the '-x' option to see each line being used. For example, 
```
#!/bin/bash -x
```

But we should probably ignore all perl stuff.  Perl handles everything better and works with unicode (i.e. utf8) from the core.

---

### Post by MAFoElffen on 2022-11-25
> **moondragon2009 said:**
> I tried this but it adds after '', 'Z:' 
 
The "," character must be being added inside $var... add another sed and strip it out...
```

sed -i -e "s/\'\'/\'Z:$var\'/g" $HOME/.config/lutris/games/PROG-12345.yml 

[s]sed -i -e "s/Z:,/Z:/g" $HOME/.config/lutris/games/PROG-12345.yml[/s]
```

---

### Post by moondragon2009 on 2022-11-29
As I said, I am not an expert, I learnt a little on my own, so excuse my ignorance. I have done other tests without success.
The file PROG-12345.yml consists of several lines, I am interested in the second one:
```
game:
  args: ''
  exe:
```
I was able to replace '' with this code:
```
sed -i "s/"\'\'"/"\'Z:$var\'"/g" $HOME/.config/lutris/games/PROG-12345.yml
``` But now I see that it only puts Z: without the variable, what can I do?

---

### Post by MAFoElffen on 2022-11-29
The sed regular edit experssions from Posts #7 and 12 work.

I can see that your original expression in Post #1 had coma's, where I can guess that you had a transcription problem and might have left one of those coma's there. Mine has no coma's.

Note that regular expression in Post #13 will not work.... It will fail on the inner double quotes, which sed will treat as ending and starting again... And will not work with a variable...

---

### Post by moondragon2009 on 2022-12-01
> **MAFoElffen said:**
> The sed regular edit experssions from Posts #7 and 12 work.

I can see that your original expression in Post #1 had coma's, where I can guess that you had a transcription problem and might have left one of those coma's there. Mine has no coma's.

Note that regular expression in Post #13 will not work.... It will fail on the inner double quotes, which sed will treat as ending and starting again... And will not work with a variable...
I understand, unfortunately I will have to find another method, in case I will let you know, thank you

---

### Post by moondragon2009 on 2022-12-02
Hi, I got some help on the Italian forum and found a solution that works well, if you want to see it here is the link: [https://forum.ubuntu-it.org/viewtopic.php?p=5320476#p5320476](https://forum.ubuntu-it.org/viewtopic.php?p=5320476#p5320476)
Thank you both again for helping me

---

