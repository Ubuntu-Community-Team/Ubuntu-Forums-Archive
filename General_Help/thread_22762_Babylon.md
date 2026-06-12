---
title: "Babylon"
date: 2005-03-29
forum: General Help
---

### Post by irad on 2005-03-29
Is there anything that is like babylon for windows but for linux, and using the database of the babylon?
 =D>  =D>  :D  :D

---

### Post by rwabel on 2005-03-29
[QUOTE=irad]Is there anything that is like babylon for windows but for linux, and using the database of the babylon?
 =D>  =D>  :D  :D[/QUOTE]

There is wordtrans ([http://www.escomposlinux.org/rvm/wordtrans/about_en.php](http://www.escomposlinux.org/rvm/wordtrans/about_en.php)) but so far it only supports the old babylon format. But they are working on the new one

and there is also stardict ([http://stardict.sourceforge.net/](http://stardict.sourceforge.net/))

take a look, they are both good in my opinion.

---

### Post by irad on 2005-03-30
[QUOTE=rwabel]There is wordtrans ([http://www.escomposlinux.org/rvm/wordtrans/about_en.php](http://www.escomposlinux.org/rvm/wordtrans/about_en.php)) but so far it only supports the old babylon format. But they are working on the new one

and there is also stardict ([http://stardict.sourceforge.net/](http://stardict.sourceforge.net/))

take a look, they are both good in my opinion.[/QUOTE]

yeah, thought so,
i need to add hebrew for it, so it won't really help me at this point,
i hope something will be released soon,

thanks alot

---

### Post by yhotg on 2005-09-05
[QUOTE=irad]yeah, thought so,
i need to add hebrew for it, so it won't really help me at this point,
i hope something will be released soon,

thanks alot[/QUOTE]

I am looking for the same thing, to add hebrew <-> english
and all the other new glosaries (that are free by the way) 
in the meantime i am using more stardict, for the english <-> english, than wordtrans
and a little of kdict 
but is not the same...
 :roll:

---

### Post by mandavi on 2006-06-25
there are dictionaries for hebrew-english for stardict - it's just they don't seem to work for me and i didn't figure out why yet.
[hebrew  - english]("http://prdownloads.sourceforge.net/xdxf/stardict-comn_sdict_axm03_Hebrew_romanized_English-2.4.2.tar.bz2?use_mirror=switch") and [english - hebrew]("http://prdownloads.sourceforge.net/xdxf/stardict-comn_sdict_axm03_English_Hebrew_romanized-2.4.2.tar.bz2?download")

---

### Post by yhotg on 2006-06-27
[QUOTE=mandavi]there are dictionaries for hebrew-english for stardict - it's just they don't seem to work for me and i didn't figure out why yet.
[hebrew  - english]("http://prdownloads.sourceforge.net/xdxf/stardict-comn_sdict_axm03_Hebrew_romanized_English-2.4.2.tar.bz2?use_mirror=switch") and [english - hebrew]("http://prdownloads.sourceforge.net/xdxf/stardict-comn_sdict_axm03_English_Hebrew_romanized-2.4.2.tar.bz2?download")[/QUOTE]

yes, i found those two romanized hebrew dict. but same thing, i don't get any definition, non translation to any word i try .
so i just use my zack dictionary, it's old, but it helps. LOL

on the other hand, when searching words on [www.answers.com](www.answers.com) sometimes there are translations to hebrew.

---

### Post by mandavi on 2006-06-28
did you maybe try to convert hebrew dictionaries from other formats to the stardict format? i found a tool which didn't compile correctly yet at [this forum]("http://xdxf.revdanica.com/forum/") called makedict. in case you succeed, please let me know. In case I will, I will write here again.

edit: what is the zack dictionary - where do i find it?

---

### Post by medya on 2007-04-27
try [stardict + dictconv]("http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html")

---

### Post by bit4 on 2008-01-09
The dictionary tools found in the standard software repository can get very close to the ease of use you get with Babylon. There are also tools that can convert old Babylon (*.DIC) dictionary files and new glossary (*.BGL) files to the formats used with open source tools. Here is the list of steps I performed in order to get a very fast dictionary lookup tool:

**- Install dictd**
dictd is a dictonary server. You don't have to install it locally, as free ones are available on the Internet, but if you want FAST response, a local server is best.

**- Install one or more dictionaries**. E.g., _dict-freedict-eng-swe_
_dict-wn_ is a very convenient english-english dictionary.
_dict-moby-thesaurus_ is a comprehensive thesaurus.

**- Install kdict**
kdict is a client (UI) for accessing the server. It was written for KDE, but I still recommend it over its Gnome counterpart because it has a command-line switch to tell it to look up the currently selected word, which enables it to be used much more conveniently than using copy/paste.

**- Associate an unused key combination with the kdict menu entry** and add '-c' to the command so that it will lookup the selected word as soon as it opens.
Associating an arbitrary keybord shortcut to an arbitrary command is possible in KDE but not in the fault Gnome window manager. I used the combination shift-esc.
The menu entry is in Office / More Applications / Online Dictionary. You can right-click on the menu entry, select Edit Item, and append -c to the command. On my system the command now looks like this:
  [INDENT] kdict -caption "%c" %i %m -c[/INDENT]
at the bottom of the Edit Item window, there is a drawing of a keyboard button. Click on it and then press shift-esc (or whatever key combination you want) to make it easy to launch no matter in what application you are.

**- Start kdict** (if you did the last step above, you can do that by pressing shift-esc) and direct it to the local dictionary server by opening the Settings menu, selecting Configure Dictionary, and replacing "dict.org" at the top with "localhost".
Again, there is no harm in not performing this step, but if you skip it, the response time will be much worse. On my machine, an Internet lookup takes several seconds, whereas a local one is instantaneous.

If you did all the above steps, you get a system where you can double-click any word on the screen (to select it) and then press shift-esc to see its definition / translation / synonyms.

If you want to use Babylon dictionaries, you can obtain old (pre-2001) *.dic files or new glossary (*.bgl) files and convert them to be used with this setting. Install and use **dictconv** (dictconv x.bgl -o x.index) for the conversion, then compress the resulting *.dict file using **dictzip**, copy the *.dict.dz and *.index files into /usr/share/dictd and finally run "sudo **dictconfig** -w" and restart dictd. (Sorry, this post is getting too long to go into more details here)
Unfortunately, I haven't found a tool to convert the newer Babylon dictionary files. Also, Hebrew poses a special challenge that I am still working on.

Hope this helps somebody out there.

---

### Post by bit4 on 2008-01-14
I managed to convert Babylon_English_Hebrew.BGL into valid dict format and use it with dictd. Here is how:

1 - Run this command to convert the BGL file into a pair of index+dict files::
```

     $ dictconv Babylon_English_Hebrew.BGL -o Babylon_English_Hebrew.index >Babylon_English_Hebrew.dict
```

This creates a defective index + dict pair of files, but all the info is in them, so they can be fixed, like this:

2 - Save the Python program at the end of this post into a file named fix_babylon_heb_dict.py

3 - Run the fix program to create better behaved index+dict pair of files:
```

     $ python fix_babylon_heb_dict.py Babylon_English_Hebrew
```

    The result is named Babylon_English_Hebrew.{index|dict}.new

4 - Compress the dict file:
```

    $ dictzip Babylon_English_Hebrew.dict.new
```

5 - Copy the pair to where dictd looks for dictionaries by default:
```

    $ sudo cp Babylon_English_Hebrew.dict.new.dz /usr/share/dictd/Babylon_English_Hebrew.dict.dz
    $ sudo cp Babylon_English_Hebrew.index.new /usr/share/dictd/Babylon_English_Hebrew.index
```

6 - Use an automated tool to recreate the dictd config file from the list of available dictionary files:
```

    $ sudo dictdconfig -w
```

7 - Restart dictd so it will use the new config file and load the new dictionary:
```

    $ sudo /etc/init.d/dictd restart
```

That's it!
I am still hoping to find a similar procedure for converting old *.DIC files as well.

Here is the fix_babylon_heb_dict.py program:
```

#
# Read the *.dict and *.index files produced from a Babylon Hebrew dictionary
# by dictconv and convert them into a valid pair of files using utf-8 encoding.
# Written by bit4, Jan 2008.
#
# The *.dict file from Babylon represents Hebrew using a range of accented
# characters starting at 0x00e0 instead of the real Hebrew range that starts
# at 0x05d0. In addition, the letter Nun is represented by 0x011f. Also,
# the index file contains funny $nnnn$ suffixes in most of the words.
# This program fixes all of the above problems.
# The input file name is given on the command line (without the suffix)
# and the output is saved into a pair of files with the same names and the
# word '.new' appended.
#
# The full process of converting and installing a BGL dictionary:
#   $ dictconv Babylon_English_Hebrew.BGL -o Babylon_English_Hebrew.index >Babylon_English_Hebrew.dict
#   $ python fix_babylon_heb_dict.py Babylon_English_Hebrew
#   $ dictzip Babylon_English_Hebrew.dict.new
#   $ sudo cp Babylon_English_Hebrew.dict.new.dz /usr/share/dictd/Babylon_English_Hebrew.dict.dz
#   $ sudo cp Babylon_English_Hebrew.index.new /usr/share/dictd/Babylon_English_Hebrew.index
#   $ sudo dictdconfig -w
#   $ sudo /etc/init.d/dictd restart
#

import re
import sys

abc='ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/'
def s2i(s):
    """Return the number represented by the base64 string s."""
    n = 0
    for c in s:
        n = n * 64 + abc.index(c)
    return n

def i2s(n):
    """Return the base64 string representing the number n."""
    s = ''
    while n:
        s = abc[n % 64] + s
        n /= 64
    return s or 'A'

def acc2heb(ch):
   if ch == u'\u011f': return u'\u05e0'
   if u'\xe0' <= ch <= u'\xff': return unichr(ord(ch) - 0xe0 + 0x05d0)
   return ch

def fix_def(definition):
    """Return the fixed definition: convert from Windows1255 to utf-8"""
    return ''.join(map(acc2heb, definition.decode('utf8','replace'))).encode('utf8','replace')

def writedef(out_idxfile, out_dictfile, word, definition, oldpos):
    """Append the given word+def to the output dictionary and return the next position"""
    deflen = len(definition)
    out_idxfile.write('%s\t%s\t%s\n' % (word, i2s(oldpos), i2s(deflen)))
    out_dictfile.write(definition)
    return oldpos + deflen

def main():
    if len(sys.argv) != 2:
        print >>sys.stderr, "Usage: %s name" % sys.argv[0]
        print >>sys.stderr, "Input is name.index + name.dict, output is name.index.new + name.dict.new"
        sys.exit(1)
    fname = sys.argv[1]

    idxfile = file(fname + '.index', 'r')
    dictfile = file(fname + '.dict', 'r')
    out_idxfile = file(fname + '.index.new', 'w')
    out_dictfile = file(fname + '.dict.new', 'w')
    outpos = 0

    outpos = writedef(out_idxfile, out_dictfile, '00-encoding', 'utf-8', outpos)
    for line in idxfile.readlines():
        word,pos,leng = line.strip().split('\t')
        pos,leng = s2i(pos),s2i(leng) #todo: add try/except and ignore lines with errors
        # Remove the weird $number$ suffix that many entries have after using dictconv on
        # Babylon glossaries.
        mo = re.match(r'(.*)\$\d+\$$', word)
        if mo:
            word = mo.group(1)
        #
        dictfile.seek(pos)
        definition = fix_def(dictfile.read(leng))
        #
        outpos = writedef(out_idxfile, out_dictfile, word, definition, outpos)

if __name__ == '__main__':
    main()

```

---

### Post by go_beep_yourself on 2008-05-09
Here's an easier way!

I've tried stardict-editor and dictconv. They both failed, and I ended up with empty files 0 bytes in size. I found this website that has all or most dictionaries already converted, ready to be downloaded, unpacked, and moved to /usr/share/stardict/dic/.

[http://xdxf.revdanica.com/down/index.php](http://xdxf.revdanica.com/down/index.php)

---

### Post by arkashkin on 2008-07-22
hello to all!
I use the real Babylon on wine 1.1.1, the 6,7 versions dont work,but the 5 version work's great. It crushes from time to time but it works.
I have followed some guide i found:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5336](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5336)


1:

Install IEs4Linux:
( [www.tatanka.com.br/ies4linux/page/Main_Page](www.tatanka.com.br/ies4linux/page/Main_Page))
wget [www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux

2:

Make a suitable bottle:
Get the ie6 map from where you installed the IEs4Linux
Copy it to wherever say /home/User/ie6
run:
WINEPREFIX="/home/User/ie6" winecfg
Change from Windows 98 to Windows XP

3:

Install Babylon-Pro
say Babylon_Setup.exe (or another filename) is in /home/User.
To start it up with your new made bottle run:
cd '/home/User'
WINEPREFIX="/home/User/ie6" wine Babylon_Setup.exe
Run threw the Wizard

4:

To run babylon you can make a sh script containing:
#!/bin/bash
cd '/home/User/ie6/drive_c/Program Files/Babylon/Babylon-Pro'
LC_CTYPE=he_IL.utf8   //if you need hebrew support
LANG=he_IL.utf8       //if you need hebrew support
WINEPREFIX="/home/User/ie6" wine Babylon.exe
exit 0

If it doesn't work try to install msxml3 using winetricks, because i have installed it before i installed babylon and i don't sure if it is a must step.
Sorry for my bad english :oops:

---

