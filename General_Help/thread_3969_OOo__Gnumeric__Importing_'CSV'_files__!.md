---
title: "OOo / Gnumeric : Importing 'CSV' files  ?!"
date: 2004-11-10
forum: General Help
---

### Post by troutrou on 2004-11-10
I am not sure if the Ubuntu forum is the place to discuss problems with applications, but since I don't know of a better place, and since it's probably supported by Ubuntu, I will try my chance...

Here goes: I have a huge file full of technical data, which are from an automotive data logger. I drove the car for one hour, whilst the data logger was recording dozens of parameters, at a rate of 10 samples per second. 
The file is made of about 36,000 lines/samples, each with 40 parameters/columns. The values are separated with a "comma" sign, as defined by the 'CSV' file format. So it's dead simple. Problem is that when I open it with either Gnumeric or Open Office spreadsheet, it won't translate it properly into a spreadsheet. They will NOT spread the various parameters/values over several columns, they will just live them all packed into one cell, just like they didn't do anything at all in fact.
I wrote a tiny test file with just 2 rows of 3 values, and it does the same, doesn't work. However, when I separate the values with a "tab" character instead of the usual comma, then oh miracle, it works ! Both Gnumeric and Open Office process it correctly.

So, how come importing a bone standard CSV file doesn't work, but it works with tabs ?! Must be a bug ! But a very annoying one, as I can't use/process my data !! :o((((

I attached a screen shot of the import CSV dialog box from Open Office. It all looks nice and easy except that it just doesn't work. As can be seen in the preview area at the bottom of the dialog, it just doesn't want to separate the values, it just keeps them all packed into the first cell/column ! :o(((

Thanks for any help....

Vince

---

### Post by WW on 2004-11-10
I put this data into a file called test.csv:

One,Two,Three
100,200,300
56.0,58.1,60.0
10.0,1001,120
34,35,99.0

and used OpenOffice.org Spreadsheet to open it.  I got the same window that you did, but the data was properly separated into cells (see the screen shot).  Are there any unusual characters in your data file?  Any double quotes (")?

---

### Post by troutrou on 2004-11-11
[QUOTE=WW]I put this data into a file called test.csv:

One,Two,Three
100,200,300
56.0,58.1,60.0
10.0,1001,120
34,35,99.0

and used OpenOffice.org Spreadsheet to open it.  I got the same window that you did, but the data was properly separated into cells (see the screen shot).  Are there any unusual characters in your data file?  Any double quotes (")?[/QUOTE]


AH !!  I fiddled a bit with my files last night and noticed something about quotes indeed ! I actually have 3 files, it turns out the one I was concentrating on, HAS double quotes to start and end each line, but the other two files do NOT have double quotes, and OpenOffice DOES work with these files ! :o)
I must have messed with my data logger logging options... my fault ! :o(
I can't see how I can remove all the double quotes now, thousands of them ! Maybe a little "script" could do that ? Can scripts open and write to text files ? Not sure... :o(

Well, more problems now : I opened one of the two files that work (that don't have double quotes then), and OpenOffice is absolutely not up to the job when it came to processing the data ! Many little details that really make it a no-no.  First, functionalities, but mostly...the speed ! It took 2 minutes to open the file, and when I tried to make a graph, it used 100% CPU load and 10 minutes later it was still hanging ! Had no choice but kill the process ! I d'ont understand, it's all instant with MS Excel ! How come there is such a huge difference in speed between Windows and Linux apps ?! I t really sucks that I have to start windows/excel just to make some graphs !!! :o((((((

Maybe there is some more technical/scientific Linux program that would do a better job, be more focused on processing and displaying technical data ? Any ideas welcome...

Vince, sooo frustrated and disappointed... :o(((

PS: Gnuméric can't import the files properly, even the ones witout double quotes. And there is no options/dialog  when opengin the file so no control over it ! :o(

---

### Post by WW on 2004-11-11
Sorry, I can't help you with the performance issues.
I have no experience working with files that big.

Here's a command that will remove the leading and trailing
double quotes from your data file:

```
 $ perl -i~ -pe 's/"(.*)"/\1/' data.csv
```

Note that it saves a copy of the original file in data.csv~.
I have only tested it on a very small file, so I don't
know if perl will have performance issues :).

---

### Post by WW on 2004-11-11
The perl command that I gave above will remove the first and last double quotes
in each line, no matter where they happen to occur.  For example, the line

Title, "Another Title", Stuff

would become

Title,Another Title,Stuff

A more conservative command is
```
$ perl -i~ -pe 's/^"(.*)"$/\1/' data.csv
```
This will only remove the first and last double quotes if they are the first and last
characters in the line, respectively.  I'm just being picky here; I suspect both
commands will have the same effect on your data file.

EDIT: I fixed the perl command.  Originally I put a backslash in front of the $, because I've run into cases where shells treat it as an environment variable.  It is not needed in Ubuntu, and in fact it won't work with the backslash.

---

### Post by troutrou on 2004-11-11
Wow, thanks for that magical script !! :o)))

Sadly, it works on a small test file....but not on my big (1MB) file ! :o(
Must be a limitation of PERL, maybe this limitation ca be set up, removed or something, I ought to post a new thread about that I guess.

It didn't create a back-up file either... my Ubuntu is really strange me thinks... :o(

I found the way to get Gnumeric to work though. The trick is, you must NOT open the CSV file ! What you must do is create a new/blank spreadsheet, then go import the data using the menu \Data\Import external data\import text file.
select the firt cell of the spreadsheet in the top left corner, and the data will be inserted there.
At first I thought gnumeric was a "cheap"/light clone of Excel or OpenOffice, but it appears I was wrong. Gnumeric was far superior to OpenOffice.org as far as speed was concerned ! I could actually make a graph. It takes 3 seconds to previex it when yo click the "preview" button, but it works, whereas OpenOffice was just hanging the machine endlessly ! Gnumriec still isn't fast enough to be practical, as for example once the graphic is done, if you want to move it, by dragging it with the  mouse a few cells to the left say, well each "stroke" of the mouse takes 15 seconds ! I think the problems looks like Gnumeric is processing ALL the data when I drag the graph over the cells, instead of only modifying the data that are actually visible in the document window ! Given the size of my file, there is a huge performance difference between the two methods ! Hopefully if I inform the Gnome Team (who are responsible for Gnumeric/Abiword I believe), this huge performance issue will be sorted for the next Gnome version, hence....the next Ubuntu release as well ! :o)

Vince

---

### Post by WW on 2004-11-11
Try this instead:
```
perl -pe 's/^"(.*)"$/\1/' data.csv > noquotes.csv
```
The data without the leading and trailing double quotes will be put in the
file noquotes.csv.  The original file data.csv will not be changed.

Maybe the "-i" option has problems with big files--but 1Mb is not really big,
so I don't know if this will make a differene.

---

### Post by troutrou on 2004-11-11
WOW !!!

This last script worked perfectly !  It processed my big file no problem, removing all quotes.
A few mouse clicks later I succesfully imported it into Gnumeric, with everything nicely presented in separate columns, ready to be processed !

Yahoo !!!! :o)

I will put your script in a SAFE place !

You are a true magician WW, thank you ! :o)))


Regards,

Vince

---

