---
title: "Renaming files with a list"
date: 2024-04-18
forum: General Help
---

### Post by etonry on 2024-04-18
I have a lot of files I'd like to rename automatically.  I've been doing it manually and it's tedious.  It's a list of pictures, with names.  I would like to add a number to the beginning of the filename, which is easy with many programs and commands.  I use Thunar for this a lot, for instance.  However, this time the numbers are not going to be in numerical order.  They are included in a list, matched to the pictures.

This is a section of the files:
Culzean Castle 2, Scotland.jpeg
Culzean Castle 3, Scotland.jpeg
Culzean Castle 4, Scotland.jpeg
Desmond Castle, Ireland.jpeg
Dolbadarn Castle, Wales.jpeg
Donnington Castle, England.jpeg
Doonagore Tower 1, Ireland.jpeg
Doonagore Tower 2, Ireland.jpeg
Doonagore Tower 3, Ireland.jpeg
Doonagore Tower 4, Ireland.jpeg

And these are the new names:
&#65279;171Culzean Castle 01, Scotland.jpeg
218Culzean Castle 02, Scotland.jpeg
503Culzean Castle 03, Scotland.jpeg
751Culzean Castle 04, Scotland.jpeg
189Desmond Castle, Ireland.jpeg
190Dolbadarn Castle, Wales.jpeg
191Donnington Castle, England.jpeg
204Doonagore Tower 01, Ireland.jpeg
456Doonagore Tower 02, Ireland.jpeg 
635Doonagore Tower 03, Ireland.jpeg
816Doonagore Tower 04, Ireland.jpeg 

Is there some way to use the second list to rename the first list?  It's not a terribly important question, but it does seem to me there should be some way to have the computer do all the hard work.

---

### Post by Holger_Gehrke on 2024-04-18
If the names in the second list are the same as the ones in the first list except for the numbers in the beginning, then you don't even need to have the first list for a script to do the renaming.
```

#!/usr/bin/env /usr/bin/bash
while read filename ; do
    oldname=${filename##[0-9][0-9][0-9]}
    mv "${oldname}" "${filename}"
done

```
This reads a filename from standard input, removes three digits (and I do mean three digits; if there are less, then nothing will be removed; if there are more, then only three will be removed and the old name generated will probably be wrong...) from the beginning to generate the old name, and then renames the old name to the new one. You'd call this with a redirection, something like 'script < filelist'.

Holger

---

### Post by etonry on 2024-04-20
Thank you for a quick reply.  I think you misunderstood what I want to do.  Your script * removes * three digits.  I want to add three digits.  If they were consecutive, I could use Thunar and have it done a long time ago.   I'm starting with files named as in the first list above.  I want to rename them to match the second list above.   The main name stays the same, but different, non-consecutive numbers, are to be added at the beginning of the filename.  I can do this in a document by concatenation, but I haven't figured out how to rename the actual files.

---

### Post by Holger_Gehrke on 2024-04-20
I assumed that you already have both (text) files, the one with the original names and the one with the new names including the numbers. I pointed out that the file with the original names isn't needed **if** the new names are the same as the original names except for the three leading digits *(which I now find to not be the case; there are some changes beyond just the added digits at the beginning, specifically an added '0' in several names)*. My script removes the digits to (re-)generate the old names and then renames from re-generated old name to the new name as read from the file. If you want to see how it works without any risk, just put an 'echo ' command at the front of the fourth line so that it reads 'echo mv "${oldname}" "${filename}"' and it will print out the 'mv' commands it would do (without the quotes which are necessary because the names contain spaces; those get swallowed by the shell while parsing the arguments).

I did it that way because it's the simplest solution and more would not be needed if the numbers at the beginning were the only change.

```

#!/usr/bin/env bash
declare -a oldnames
declare -a newnames
mapfile -t oldnames < $1
mapfile -t newnames < $2
if [[ ${#oldnames
[*]} != ${#newnames
[*]} ]] ; then 
  echo lists are not the same length; aborting
  exit
fi
for (( i=0 ; i<${#oldnames} ; i++ )) do
  mv "${oldnames[i]}" "${newnames[i]}"
done

```

This script needs the filenames of the two lists as parameters, the name of the list with the old names first. It expects the lists to have the same number of lines (it checks and aborts if that's not the case) and to be aligned with each other (so whatever is on e.g. line 20 of the file given as the first parameter gets renamed to whatever name is given on line 20 of the file given as the second parameter).

Holger

---

### Post by etonry on 2024-04-27
Ah, now I see our problem, we're talking past each other. You assume I have two text files and want to make one look like the other.  I have only one text file, the one with the new names.  The first list above is the actual list of filenames from my directory.  I want to rename these files by adding these non-consecutive numbers.

I assumed there was some simple way to let the computer do this work.  I can do it manually, but it's tedious.  Thunar lets me add consecutive numbers almost instantly.   But it won't handle non-consecutive numbers.  I've used computers for decades and Ubuntu for almost half that time.  I've just never needed to do something like this.  Is there some sort of "for x, do y" thing that'll help me?

---

### Post by dragonfly41 on 2024-04-27
This is the question I posed to my AI assistant.

[INDENT][I]Consider in Ubuntu viewing a directory of files perhaps with jpeg extensions. There is a separate text list of files where each filename matches a file in the Thunar directory but with an integer prefix of 3 numerals. Suggest a Thunar addon which can run through the directory of files, one by one, and rename to the nearest match in the text list. Indicate an error if files do not match.
[/I][/INDENT]

I don't want to keep giving AI assistants results since it might breach terms of usage .. but a Python script is suggested and there is reference to Thunar Bulk Renaming Utility.

If you are stuck I will gamble and post the advice.

---

### Post by dragonfly41 on 2024-04-27
Here is a starter.
[https://docs.xfce.org/xfce/thunar/bulk-renamer/start#:~:text=Thunar%20includes%20a%20bulk%20renamer,..%20from%20the%20main%20menu](https://docs.xfce.org/xfce/thunar/bulk-renamer/start#:~:text=Thunar%20includes%20a%20bulk%20renamer,..%20from%20the%20main%20menu).

This can be automated by referring to a list of files and finding nearest match not exact match.

Leverage regex expressions.

---

### Post by Holger_Gehrke on 2024-04-27
Yeah, we're talking past each other. My first solution (post #2) did just what you are saying now. It took the names from the file, removed the three digits at the beginning of the (new) name to get the name the file has on disk and then renamed that file to the name it found in the file. The 'mv' command **needs** the old name of the file to rename it, how else is it going to know what file to work on ? But you said you didn't want to remove digits, you want to add them ...

Another solution would be to generate a script for the renaming
```

ls *jpeg|sed 's/^\(.*\)$/mv "\1" "\1"/'>scriptfile

```
This script would then have one line per file looking like:
```

mv "Culzean Castle 2, Scotland.jpeg" "Culzean Castle 2, Scotland.jpeg"

```
You would then edit this file in a text editor to add the numbers to the second name (the new name to be given to the file). Once you have edited all the new file names in there and possibly removed the files you don't want to rename, you can run the script either by making it executable with chmod and calling it or by running 'bash scriptfile'.

If there's some logic to the numbers you want at the beginning of the names, please state it because then it might be possible to generate the numbers automatically; otherwise a boring typing job is what it is.

Holger

---

### Post by dragonfly41 on 2024-04-28
I don't know the scope of your project but I suspect that you might be better rethinking your indexing plan. Your choice of mixed numeric and text is rather odd and you might be going down a rabbithole.

I would start from the premise that you need to access web assets across several countries even if they end up in a desktop or printed mode (say using Scribus desktop publication).

Install Zotero used by professionals.

Then the assets in Zotero collections can be accessed through public/private collections .. and/or .. within Ubuntu desktop.

In other words create vectors (hyperlinks) between web assets and desktop assets.

Your Culzean Castle images (et al) will be held in Zotero private repository. To pull them into desktop apps, leverage Zotero plugins.

---

### Post by The Cog on 2024-04-28
How about this:
Pass your list of required names through this ugly awk command and save the output to required_commands:
**[FONT=Courier New]cat required_names | awk '{q="\047"}{new=$0}{sub(/^[0-9]*/,"")}{sub(/\y0+/,"")}{print("mv "q $0 q" "q new q)}' > required_commands[/FONT]**
examine required_commands to see if it's right. If so execute them with 
**[FONT=Courier New]cat required_commands | bash[/FONT]**

---

### Post by &amp;KyT$0P# on 2024-04-28
Would [FONT=Courier New]qmv[/FONT] (from [FONT=Courier New]renameutils[/FONT] package) help here?  Especially if your list of desired filenames is in the same order that [FONT=Courier New]qmv[/FONT] displays the original filenames?

---

### Post by Alxl on 2024-04-28
with all due respect to what was said so far (and I hardly understand any), it took me less than a minute to do thsi:

  	 	 	 	  [LEFT] [SIZE=5][COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]171Culzean Castle 01, Scotland.jpeg
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]218Culzean Castle 02, Scotland.jpeg
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]503Culzean Castle 03, Scotland.jpeg[/FONT][/COLOR][/SIZE]
[/LEFT] [LEFT] [SIZE=5]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Desmond Castle, Ireland.jpeg
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Dolbadarn Castle, Wales.jpeg[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Donnington Castle, England.jpeg
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Doonagore Tower 1, Ireland.jpeg
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Doonagore Tower 2, Ireland.jpeg
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Doonagore Tower 3, Ireland.jpeg[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Doonagore Tower 4, Ireland.jpeg[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]And these are the new names:
[/FONT][/COLOR]
[/SIZE][FONT=Lohit Devanagari][SIZE=5][COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]&#65279;[/FONT][/COLOR][/SIZE][/FONT][SIZE=5][COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]171Culzean Castle 01, Scotland.jpeg
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]218Culzean Castle 02, Scotland.jpeg
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]503Culzean Castle 03, Scotland.jpeg


and it will take me another minute to copy the desired names and place them on the highlighted 

"undesirable " names (one by one).
[/FONT][/COLOR][/SIZE]
[/LEFT]

---

### Post by The Cog on 2024-04-30
Yes, sometimes just doing things by hand can be the quickest. But there are apparently "a lot" of files to rename. Judging by the list shown, I would guess one to two hundred.
And finding a solution to that was easily as interesting as doing another sudoku puzzle on a Sunday morning.

---

### Post by TheFu on 2024-04-30
Just saw that halogen2 made the suggestion below, but since I'd already typed it, perhaps from a different angle, it will add to understand the tool?

**qmv** will use any editor you like and has 2 columns, A, B.  
A is the current filename.
B is the desired filename.
When the text file has all the new names you want in column B, quit/save and the rename will happen.  Any temporary collisions are handled, but if 2 files get the same name, it will not rename any of them until that is fixed.  Use whatever editor you like.  With vim, you can easily merge the file with the new names into column B.

This will probably save a step, since there isn't really a pattern to the new filenames.

When it comes to scripting this stuff, filenames with spaces and other non-alphanumeric characters, often cause scripting issues. You'll need to be extremely cautious with how you parse any inputs.

I do both scripted renaming and use qmv, almost daily for many thousands of files since I started.

---

### Post by etonry on 2024-04-30
This does look promising. I'm going on vacation next week and may not have time to try it before I leave.  I have used computers for more than forty years, all sorts, many systems.  I'm not afraid of trying to do stuff in the terminal, but I'm not overly knowledgeable about some of the commands and how to do things.  I tend to learn what I need, when I need.  This particular need has never come up before.

The "logic" of what I want to do is simple.  I like pictures of castles.  I have a large collection of such pictures.  The list is alphabetical of course.  What I want to do it use these pictures for a slide show, without getting twenty pictures of the same castle before seeing the next one.  That's what the numbers are for, to re-organize the pictures.

---

### Post by etonry on 2024-04-30
This looks good, too.  I think.  As I said above, I'm not well-versed in command line work.  I don't actually understand anything you wrote, but I'll try it.  Probably after my vacation.  Thank you for your help.

---

### Post by dragonfly41 on 2024-04-30
> [COLOR=#000000]The "logic" of what I want to do is simple. I like pictures of castles. I have a large collection of such pictures. The list is alphabetical of course. What I want to do it use these pictures for a slide show, without getting twenty pictures of the same castle before seeing the next one. That's what the numbers are for, to re-organize the pictures.[/COLOR][COLOR=#000000]

Now that you have specified requirements in full, one suggestion is that you use Zettlr as your editor (markdown). You can embed links to castles wthin your markdown code. that is each slide.  You can navigate in two directions. Left <-> Right arrows, and in fragments up and down. So a slide might relate to a castle but "fragments" (north south navigation) can hold different scenes with child notes. A two directional slide show.  Embedding images is explained in Zettlr manual.

The powerful feature in Zettlr which migh help you is export to Reveal.js. This gives the slideshow you want.[/COLOR]

---

### Post by TheFu on 2024-04-30
I do something similar with my photos, but rather than trying to organize them too much with filenames, I keep them in order by leaving the numeric sequence alone.  I will add metadata to the EXIF fields with different locations and keywords to help find them later.  

I have very few rules about photo organization.  #1 is that I'll never trust any external tool with extra information. I've been burned.  I want the filename and the embedded metadata to contain everything.  That metadata can be searched later for keywords, so if any specific location is important, I'll use the "Sub-Location" EXIF field for that.  I also try to have the GPS coordinates correct as possible.  For example, 

```
165-Hotel_Simple_Patagonia_Views-best.jpg
Create Date                     : 2017:11:25 16:52:34
City                            : Puerto Nagales
Sub-location                    : Condor Views
Province-State                  : 
Country-Primary Location Name   : Chile

```
That specific image doesn't have GPS, since I wasn't using a GPS to track at the time, but the filename has the location, which is at GPS: -51.695356, -72.527458
The Plus Code is : 8F3F+W5 Natales, Chile

Anyway, there are map tools that can show all the images with embedded GPS coordinates that are nearby.  I use this with Nextcloud Maps/Photos to see locations on a map, then click on a specific icon to see the full photo and all EXIF for it.

---

### Post by Holger_Gehrke on 2024-04-30
Most slide show programs can work of a list of files to show. For example 'feh' has an option '-f ' which will take a file that contains a list of image files one file per line which it will then proceed to show. No need to do any renaming. Even better, you can start feh with an empty or non existing playlist but give it the images that are candidates for the playlist on the command line (e.g. 'feh -f emptyplaylist.txt *.jpg') and then go through the slideshow and just hit the 'del'-key on any image you don't want in the slide show and it will automatically save the list when you exit.

Holger

---

### Post by etonry on 2024-04-30
Thank you very much for your suggestion.  It worked almost perfectly.  The first time I tried it, it failed because the command script put an extra zero in the numbers of the original files, so it couldn't find them.  I fixed that. When I ran it again, it changed almost all the filenames.  I still have about a dozen I'll have to do manually, but that's a huge improvement.  Thanks again.

---

