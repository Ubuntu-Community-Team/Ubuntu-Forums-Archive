---
title: "Yet another request for help with sed, grep and the like."
date: 2016-11-14
forum: General Help
---

### Post by texpat on 2016-11-14
I'm being asked to help with migrating of some html code from one CMS to another. I have the problem that I'm trying to read an attribute value and substitute it into that of another attribute. I'll try and illustrate:

```
<TAG1 ... rel="quite-a-long-string-with-all-sorts-of-characters" ...>
<TAG2 ... title="this-i-want-to-grab-and-substitute-into-the-rel" ...>
</TAG1></TAG2>
```

So I want to delete the contents of the rel-attribute, read the value of the title-attribute and write it to the rel-attribute. I've been messing around with sed and grep, but I can't seem to get it right. I'd really appreciate any help or hints you may have for me. I am not a programmer, so please bear with me if I use the wrong terms for things or have not given enough information.

As always, thanks for reading
Tx

---

### Post by nikefalcon on 2016-11-15
Just a suggestion..You might be better off(depending on the size and complexity of your markup.) not using regular expressions in this case. Might I recommend BeautifulSoup - it's a python library for parsing HTML and would be quite apt and also render your script extensible in case modifications are required in the future. I'm sure there are are such libraries in other languages if Python isn't your thing.

Good luck!

---

### Post by texpat on 2016-11-15
@nikefalcon: I'll definitely look into that if standard tools don't get me any further.

---

### Post by texpat on 2016-11-15
So I've grepped, sedded and awked my way to isolating the necessary strings and storing them in variables, like such:

```
TOBEREPLACED contains rel="quite-a-long-string-with-all-sorts-of;-[special]:pesky-characters"
REPLACEWITH contains title="this-i-want-to-grab-and-substitute-into-the-rel"
```

Note that the '=' and quotation marks are all part of the string.
Testing this by echo-ing to the console, all looks fine. However, when I

```

sed -i -e 's/$TOBEREPLACED/$REPLACEWITH/g'

```

it does nothing. I know it probably has to do with all those special characters. I tried using double quotes, combinations of single and double quotes and other stuff suggested over at [askubuntu]("http://askubuntu.com/questions/76808/how-do-i-use-variables-in-a-sed-command") and [stack overflow]("http://stackoverflow.com/questions/19151954/how-to-use-variables-in-a-command-in-sed"), but either I'm doing it wrong or I don't understand the issue properly.

Any help wold be greatly appreciated
Thanks
Tx

---

### Post by dragonfly41 on 2016-11-15
Perhaps .. use double quotes to expand variables in command ..

[http://askubuntu.com/questions/76808/how-do-i-use-variables-in-a-sed-command](http://askubuntu.com/questions/76808/how-do-i-use-variables-in-a-sed-command)

---

### Post by texpat on 2016-11-15
Hi @dragonfly41: Yes, I tried that, but no fun. I have whitespace (blanks) and semicolons in the string which are making the command difficult to implement.

---

### Post by dragonfly41 on 2016-11-15
My next suggestion is that you use an online regex validator to test your commands

here is just one I found .. there are many .. [http://www.regextester.com/](http://www.regextester.com/)

---

### Post by vasa1 on 2016-11-15
> **nikefalcon said:**
> Just a suggestion..You might be better off(depending on the size and complexity of your markup.) not using regular expressions in this case. Might I recommend BeautifulSoup - it's a python library for parsing HTML and would be quite apt and also render your script extensible in case modifications are required in the future. I'm sure there are are such libraries in other languages if Python isn't your thing.

Good luck!
+1 to that. For more views on the matter: [http://stackoverflow.com/questions/1732348/regex-match-open-tags-except-xhtml-self-contained-tags](http://stackoverflow.com/questions/1732348/regex-match-open-tags-except-xhtml-self-contained-tags)

---

### Post by texpat on 2016-11-15
Thanks for those pointers dragonfly41 and vasa1. Regular expressions are indeed not good for parsing HTML; that stack overflow post is a bit of a classic ;-) I'm trying to get away with it anyway because I'm doing a one-off thing and a quick and dirty hack is all I need and I'm not a programmer, so I have very limited resources. Putting together something in python or perl is not off the books, however, since the problem is starting to become icky. I managed to get my strings together and now [FONT=Courier New]**sed**[/FONT] is acting up when I try to run those through it...:confused:

So if anyone has any idea how I can make [FONT=Courier New]**sed**[/FONT] work with my strings in variables, I'd really like to hear about it.

---

### Post by steeldriver on 2016-11-15
IMHO you'd be more likely to get helpful responses if you post a concrete example - just telling us that your have "quite-a-long-string-with-all-sorts-of-characters" and sed is "acting up" isn't really much to go on

In some cases you may be able to use perl's quotemeta as near drop-in replacement for sed, for example

Given

```
$ pat='all-sorts-of;-[special]:pesky'
$ rep='XXX'

```
Then

```
$ echo 'quite-a-long-string-with-all-sorts-of;-[special]:pesky-characters' |  sed "s/$pat/$rep/"
quite-a-long-string-with-all-sorts-of;-[special]:pesky-characters

```
whereas

```
$ echo 'quite-a-long-string-with-all-sorts-of;-[special]:pesky-characters' |  perl -pe "s/\\Q$pat/$rep/"
quite-a-long-string-with-XXX-characters
```

---

### Post by dragonfly41 on 2016-11-15
If you wish to continue using sed (notwithstanding the stack overflow warnings) then one tip I have used is to pre-parse your original source (html) and your search pattern.

e.g. on a first pass find all spaces (white space) in your original source (html) and replace with "\&nbsp;" .. this gets rid of white space.

Then apply your sed command.

The principle is to (temporarily) substitute characters such as space.  You can apply this pre-parsing to element names to basically convert html into a _raw text string_.

Of course you will have to *reverse* this process after your substitution so you must use unique strings which do not otherwise appear in the original html.

Rough example .. find "<tag" and change to (say) "£$tag" .. apply sed find/replace .. find "£$tag" and replace with "<tag".

This is a three stage process.


[p.s.] sed reference [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)


[p.p.s] As an added note, with html parsing, try a sed separator other than "/" .. 

[http://stackoverflow.com/questions/16778667/how-to-use-sed-to-find-and-replace-url-strings-with-the-character-in-the-tar](http://stackoverflow.com/questions/16778667/how-to-use-sed-to-find-and-replace-url-strings-with-the-character-in-the-tar)

---

### Post by texpat on 2016-11-15
As steeldriver suggested, I'll try to be more specific.

The HTML file contains several blocks of code like the one below.

 ```
 1 <div class="span4">
 2 <span style="display: inline-block;" class="wf_caption">
 3 <a type="image" class="jcepopup" target="_blank" rel="group[manuals];title[mycompany manuals::]" href="images/articles/manuals/01-mycompany-manuals.jpg">
 4 <img class="thumb" style="margin: auto;" title="Manuals are available." alt="Manuals are available." src="images/articles/manuals/01-mycompany-manuals-thumb.jpg" />
 5 </a>
 6 <span class="nr_caption" style="clear: both; display: block;">Manuals are available.</span>
 7 </span>
 8 </div>
```

I want to substitute the expression [FONT=Courier New]**rel="..."**[/FONT] on line 3 with the expression [FONT=Courier New]**title="..."**[/FONT] from line 4. Line 4 remains untouched.

After quite some mucking about I came up with the following code to read these expressions into variables like so:

```
OLD=$(cat "$filename" | grep -o 'rel="group.*' | sed 's/\ href=.*//g')
NEW=$(cat "$filename" | grep 'img class="thumb"' | grep -o 'title=.*' | sed 's/\ alt=.*//g')
```

so I thought I could do:

```
 sed 's/$OLD/$NEW/' or sed "s/$OLD/$NEW/" or even 's/'"$OLD"'/'"$NEW"'/' (I may have gotten that last one wrong, though).
```

But that&#8217;s only half the problem. Turns out the variables contain the whole list of all occurrences of the match in the whole file. So if I have three blocks of code like the above, 
```
OLD will contain

rel="group[manuals];title[mycompany manuals::]
rel="group[manuals];title[mycompany manuals::]
rel="group[manuals];title[mycompany manuals::]

and NEW will contain

title="Manuals are available."
title="Manuals are available."
title="Manuals are available."
```

with line breaks and all. So when I echoed the variables, it looked as if they were individual values, but they are not. No wonder sed wasn't doing anything. Although I still don't know whether it is because it can't find a match or because of all those semi-colons, colons and line breaks...

---

### Post by dragonfly41 on 2016-11-17
I don't know if you have now solved your problem.
But if not I suggest that you approach this by parsing your html file .. line by line in a simple python script.

First remove the "\n" (new line) before "<img" and before "</a>" so that the string "<a  ... </a> appears as one line and not several lines.

Then you can use python split() method to split that line creating an array of parts. 
You then continue to split parts of the array until you have isolated the strings you wish to juggle around to reconstruct the line..

You then concatenate a new line from the split parts.

The split delimiters (to create different arrays) can be split("rel=") and split("title=").


Here is an example ...

Before splitting and reordering parts of array ...

```

<a type="image" class="jcepopup" target="_blank" rel=[COLOR=#ff0000]"group[manuals];title[mycompany manuals::]"[/COLOR] href="images/articles/manuals/01-mycompany-manuals.jpg"><img class="thumb" style="margin: auto;" title=[COLOR=#0000ff]"Manuals are available."[/COLOR] alt="Manuals are available." src="images/articles/manuals/01-mycompany-manuals-thumb.jpg" /></a>.

```

After splitting and reordering parts from multiple arrays ...
```

<a type="image" class="jcepopup" target="_blank" rel=[COLOR=#0000FF]"Manuals are available." [/COLOR]href="images/articles/manuals/01-mycompany-manuals.jpg"><img class="thumb" style="margin: auto;" title=[COLOR=#0000ff]"Manuals are available."[/COLOR] alt="Manuals are available." src="images/articles/manuals/01-mycompany-manuals-thumb.jpg" /></a>

```

---

### Post by steeldriver on 2016-11-17
IMHO if you're going to step up to python, you may as well go the hole hawg and do something like

```

#!/usr/bin/python

from lxml import etree

with open('file.html', 'r') as f:
    tree = etree.parse(f)

root = tree.getroot()
imgLink = root.find(".//a[@type='image']")
imgTitle = root.find(".//img").get('title')

imgLink.set('rel', imgTitle)

print etree.tostring(root)

```

Testing

```

$ ./fixrel.py
<div class="span4">
<span style="display: inline-block;" class="wf_caption">
<a type="image" class="jcepopup" target="_blank" rel="Manuals are available." href="images/articles/manuals/01-mycompany-manuals.jpg">
<img class="thumb" style="margin: auto;" title="Manuals are available." alt="Manuals are available." src="images/articles/manuals/01-mycompany-manuals-thumb.jpg"/>
</a>
<span class="nr_caption" style="clear: both; display: block;">Manuals are available.</span>
</span>
</div>

```

---

### Post by texpat on 2016-11-30
Hi steeldriver, and my apologies for not getting back sooner. I was away for a few days and in the mean time the briefing changed, so the concrete issue of this thread is no longer acute. Nevertheless, your hints are definitely worth looking into for some other, related tasks I have at hand right now. However, I balk at using python, since I have zero experience with it. I did some remotely similar stuff with perl, but that was ages ago. Still, I think I'll try to brush up on that rather than learning something I know nothing about at all.

It looks as if [FONT=Courier New]**sed**[/FONT] has issues that prevent me form using it for more complex substitutions - my ability to wrap my mind around it may be part of it, though. For example, I seem to have problems removing newlines...

My basic problem remains:

I have a list of substitutions to perform on a file or a number of files and the seemingly simple [FONT=Courier New]**s/$OLD/$NEW/**[/FONT] turns out to be a hard nut to crack for me. 

Any questions I'll post to a new thread so as not to overload this one which is, to all practical effects, obsolete.

Thanks to all for reading and contributing
Tx

---

