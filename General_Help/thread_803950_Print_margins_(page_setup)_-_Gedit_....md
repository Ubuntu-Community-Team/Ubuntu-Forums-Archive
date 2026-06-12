---
title: "Print margins (page setup) - Gedit ..."
date: 2008-05-22
forum: General Help
---

### Post by gstuart on 2008-05-22
I've searched for the solution to this: After upgrading from 6.06 LTS to 8.04 LTS, my print pargins (Claws Mail; Gedit) have shrunk to ~1/4-inch!

I've searched (Google; these forums - refer below) for the solution, but none of the suggested solutions have worked, or are acceptable for routine use.

For the life of me, I cannot understand how the Gedit page setup dialog box doesn't allow one to explicitly define print margins (likewise Claws mail, which uses Gedit, I believe).!

Any solutions?  Thanks ...  :-)

 ==============================================

localhost:631

 ==============================================

[http://ubuntuforums.org/showthread.php?t=527485](http://ubuntuforums.org/showthread.php?t=527485)

Re: Print margins in Gedit

Quote: When printing from Gedit, I can choose the paper size (A4 in my case), but can I also set the margins? By default the top and bottom margins are much too large for my taste (3.1 cm whereas the left margin is just 2.1 cm).

I've got the same problem. Because there's no way to config print margins via user interface it is necessary to edit the printing config file on

Code:

~/.gnome2/gedit-print-config

There you can edit the key with id "Margin". After defining the desired print margins it is necessary to close all gedit instances an restart it. If it takes no effect already, please log off and log in again. This workaround is user specific, so you can define separate printing properties for each user.

 ==============================================

[http://home.att.net/~Tom.Horsley/linux-tidbits.html](http://home.att.net/~Tom.Horsley/linux-tidbits.html)

lpoptions 

 ==============================================

[http://osdir.com/ml/linux.redhat.release.psyche/2002-10/msg01383.html](http://osdir.com/ml/linux.redhat.release.psyche/2002-10/msg01383.html)

You can use qtcups to set the page margins for text output at least.

(Or equivalently, use 'lpoptions' to set the page-top, page-left,
page-right and page-bottom options.)

 ==============================================

[http://linux.derkeiler.com/Mailing-Lists/Debian/2008-04/msg02676.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-04/msg02676.html)

The "pr" command may be of help to you.

 -------------------------------

Thanks for your suggestion.

Well, it's strange: if I do:

$ pr filename

, the chinese characters included in the document are wonderfully shown on the
terminal; but if I do:

$ pr filename | lp

they are not printed.

Any idea of how to work the problem out? I have Debian Etch.


 ==============================================
[http://machine-cycle.blogspot.com/2007/09/printing-plain-text.html](http://machine-cycle.blogspot.com/2007/09/printing-plain-text.html)
September 23, 2007
Printing Plain Text

Last time I wanted to print a document I got bitten quite hard. This time I was ready. Or so I thought. I mean, all I wanted to do was print a plain text document ... Way back when, during my time at the university, we used to print stuff with lpr, so I tried it out, and realized that it doesn't wrap around lines that are longer than the paper width. The document at hand contained newline characters only after each paragraph - it looked OK on screen, but horrible when printed out.

Well, I tried printing from within gedit (the default GNOME editor). It performs text wrapping on long lines at word boundaries, which is nice. But:

    * it prints the file name and page numbers on every page - and I couldn't find an obvious way to turn this feature off
    * there doesn't seem to be a simple way to insert a page break
    * it does not interpret or honor pagefeeds (^L characters) that are often used in plain text documents as page breaks

Next I tried gtklp: it can be made to wrap long lines, but not at word boundaries, so words get cut up between lines.

How about emacs? open the file, mark the whole document by hitting Ctrl-x-a , and then hit Meta-x (Alt-x on normal PC keyboards) and type fill-region - this does line wrapping at word boundaries, which makes the document printable with gtklp, or directly from emacs.

Except that region filling in emacs does some unexpected things - like indenting a whole paragraph if the first word is indented (I wanted just the first line to be indented). I could fix it by hand, but that didn't seem like the Right Thing To DoTM. There's probably a way to change this behavior, but I didn't bother looking for it.

I vaguely recalled using a2ps to convert plain text documents to PostScript, so I installed the a2ps package, read the manual page, and realized it didn't do line wrapping at word boundaries. Sigh. So I searched for "word wrap a2ps", in the hope that I was missing something, and hit a blog entry which pointed to enscript as the right tool for the job.

The following command line does exactly what I want:

enscript --header='||Page $% of $=' --margin=72:72:72:72 -1 --word-wrap --media=A4 file.txt

(one inch margins on all sides, 1 up, word wrap, A4 page size, right aligned header showing page info)

Sheesh...

 ==============================================

[http://www.bobrankin.org/rhl06.htm](http://www.bobrankin.org/rhl06.htm)
Important Linux Commands

Customizing Your Printouts

The lpr command is a no-frills way to print your files. It doesn't do any fancy formatting; it just dumps your file on the printer. If you'd like to format your printout (paginate, add a title, set margins, or control the page length), you can use the pr command in conjunction with lpr. By default, pr will add page numbers and a title consisting of the file's name and the date and time it was last modified. But you can do lots of other fancy formatting as well. Here are some of the options that pr supports:

-d   Double-space the printout.

-h <my title>   Specify a title for the page header (the default is the file name).

-Ln   Set the page length to n lines (the default is 66).

-On   Set the margin to n characters (the default is 8).

-T   Suppress the page header.

-2 | -3 | -4   Print output in two, three, or four columns (as in a newspaper).

Typically, the output from pr is sent only to your printer (by piping the output to lpr, as shown in the following examples), but if you leave off the lpr step, you'll see the output on the screen instead. Here are some examples using the pr command to print a file named panda97.txt--for example, with no options specified, just adding page numbers and the default title (file name and date):

pr panda97.txt | lpr

Here we've specified a more meaningful title for the printout:

pr -h "Financial Report" panda97.dat | lpr

And now we've set the page length to 55 lines, set the margin to 5 spaces, and added double-spacing:

pr -h "Financial Report" -l55 -o5 -d panda97.dat | lpr

Stop the Presses!

If you send a file to the printer by mistake, you might be able to snatch it from the print queue before it's too late. First use lpq to find the job number:

lpq
Rank Owner Job Files Total Size
1st hermie 17 really-humongous 2317678 bytes

In the example shown here, the job number is 17. Once you know the job number, enlist the assistance of lprm to remove that file from the queue as follows (using job 17 as an example):

lprm 17

 ==============================================

[http://ubuntuforums.org/archive/index.php/t-187975.html](http://ubuntuforums.org/archive/index.php/t-187975.html)

#---------set the margins of the printed page-------------------
# Margins: these are distances from the edges of the paper in
# "dots" ( 600 dots = 1 inch = 2.54 cm). 
# Nothing outside these margins will be printed. 
# Default values are give below; uncomment and change, if necessary. 
# (Older versions of pnm2ppa required larger left and right margins to avoid 
# printer failure with "flashing lights", but this problem is believed to 
# be solved)

#topmargin 10 
#bottommargin 150
#leftmargin 10
#rightmargin 10

 ==============================================

[http://osdir.com/ml/gentoo.desktop/2006-08/msg00006.html](http://osdir.com/ml/gentoo.desktop/2006-08/msg00006.html)

Re: Galeon, Firefox and printer margins

In Firefox, you can specify the distance from the headers to the paper edge in either about:config or in the printer preferences dialog, so no other tools are needed.  My problem is with Galeon.  I only mentioned Firefox as an example of a browser in the same family that _does_ allow this setting.

 ==============================================

[http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&comments_parentId=40579&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&comments_parentId=40579&forumId=1)

The way to do this in Firefox Beta is to do it under Page Setup. You have to make a Custom Page Setup and the Select that. Not very intuitive.

Tue 06 of May, 2008

How to set margins on Linux host:
1. File->Page Setup
2. Paper Size->Manage Custom Size
3. Enter Margins and Close
4. Select new custom setting

 ==============================================

[http://ubuntuforums.org/showthread.php?t=278836](http://ubuntuforums.org/showthread.php?t=278836)

Change printer margins?

I've had many problems with my samsung ml-2010 laser printer running on ubuntu. from what i've heard it works on other distros, just not ubuntu. is there some kind of way to compensate for the marginal errors? one workaround is adjusting page setup before printing every single time, but i was wondering if there was a better way or maybe a permanent adjustment as such. i need help!

Have you tried:
Code:

# replace printername appropriately; sets top margin to 0.5" (36 pts.)
# also use page-left, page-right, page-bottom.
lpoptions -p printername -o page-top=36

Enter at a shell prompt
Code:

user@ubuntu:~$ lpoptions -p printername -o page-top=36

 ==============================================

---

### Post by AmpersUK on 2011-11-06
Read through all this and it has really helped me.

I am dumping GEdit for something that works easily.

---

### Post by oldos2er on 2011-11-06
Closed, please don't bump old threads.

---

