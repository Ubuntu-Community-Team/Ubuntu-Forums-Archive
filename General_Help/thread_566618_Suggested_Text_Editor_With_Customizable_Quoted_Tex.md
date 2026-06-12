---
title: "Suggested Text Editor With Customizable Quoted Text and Word-Wrap For Linux?"
date: 2007-10-03
forum: General Help
---

### Post by StewartM on 2007-10-03
Hello,

What I'd like is a simple text editor that:

a) allows me to set the word wrap settings to whatever character length I want (and to hard-wrap it as well);

b) allows me to "paste as quoted" text (using the '>' sign conventions) and allows me to copy it to another application.

Of what Ive found in the standard Ubuntu repository, just in the text manipulation aspect of other programs:

1) Gedit doesn't do this;
2) Evolution doesn't allow you to copy the '>'s when "paste as quote" to transfer;
3) Pan doesn't allow you to either "paste as quote" in composing a message or set the word wrap to anything else than 80.

In Windows-world, I ended up using a combination  Forte Free Agent newsreader's text editor to do this, or XNews newsreader, which they did more or less. I could run these under WINE, i guess. They both have limitations, XNews won't let you wrap less than 65 characters per line and while Free Agent will wrap text at whatever character length you prescribe, it won't do the "paste as quote" thing and wrap it with the the r ">"s preceding each line.

But certainly there is a text editor somewhere that will do this. 

I want to use this to comment on blogs, so I can quote text and also wrap it to fit within the text box (which can vary greatly in blog-land) without ugly line breaks.

Stewart

---

### Post by StewartM on 2007-10-08
> **StewartM said:**
> Hello,

What I'd like is a simple text editor that:

a) allows me to set the word wrap settings to whatever character length I want (and to hard-wrap it as well);

b) allows me to "paste as quoted" text (using the '>' sign conventions) and allows me to copy it to another application.

Of what Ive found in the standard Ubuntu repository, just in the text manipulation aspect of other programs:

1) Gedit doesn't do this;
2) Evolution doesn't allow you to copy the '>'s when "paste as quote" to transfer;
3) Pan doesn't allow you to either "paste as quote" in composing a message or set the word wrap to anything else than 80.

In Windows-world, I ended up using a combination  Forte Free Agent newsreader's text editor to do this, or XNews newsreader, which they did more or less. I could run these under WINE, i guess. They both have limitations, XNews won't let you wrap less than 65 characters per line and while Free Agent will wrap text at whatever character length you prescribe, it won't do the "paste as quote" thing and wrap it with the the r ">"s preceding each line.

But certainly there is a text editor somewhere that will do this. 

I want to use this to comment on blogs, so I can quote text and also wrap it to fit within the text box (which can vary greatly in blog-land) without ugly line breaks.

Stewart


I'm finding out that running Pegasus mail version 3.12 under WINE is providing me exactly what I want (both customizable word wrap length and "paste as quote" using '>'s) , but I still would like a native Linux text editor that does this trick. So I'll leave this thread open to see if someone suggests something. 

I mean, I'd hate to download and install and try a bunch of text editors that don't work if I don't have to. I've tried checking out them over the web but if this is a feature of any of them, no one is advertising it.

Stewart

---

### Post by stanabe on 2008-02-15
**[SIZE="4"]Applying Hard Wraps / Line Breaks[/SIZE]**

You might want to try this: 

1. Open gedit 
2. Edit -> Preferences -> Plugins 
3. Enable "External Tools" and press "Configure Plugin" 
4. Press "New" and enter "Line Break at Col 50" (or any name you like) 
5. Paste the following code in the "command(s)" text area: 

```
#!/usr/bin/env python

import sys

breakat = 50 # change this to desired length

for line in sys.stdin.readlines():
	newline = ''
	for word in line.split() + ['\n']:
		if word == '\n':
			print newline
		elif len(newline + word) > breakat:
			print newline
			newline = word + ' '
		else:
			newline = newline + word + ' '
```

6. Choose "Current selection" as Input 
7. Choose "Replace current selection" as Output 
8. Close "External Tools Manager"  by pressing the "Close" button
9. Now this script is executable under the "Tools" menu. Make sure you first select the text that you want to apply line breaks. Otherwise it seems the script is applied to the whole document (This might be a bug...).

[B]
[SIZE="4"]Adding Arbitrary Letters in Front of Quotes[/SIZE][/B]

With regard to quotes, you can do the following:

1. Enable "Indent Lines" plugin
2. Copy and paste the text that you want to quote
3. Select the text and press (Ctrl - t). This will indent the multiple lines that you selected.
4. Press the "Replace" button and enter the following:
```
**Search for:** \t
**Replace with:** > 
```
("\t" means tab character, and "> " can be anything, like "*lastname*>> ")
5. Choose "Replace all"


Better codes/ideas, anyone? 

- Satoshi

---

### Post by stephenb on 2008-03-03
Thanks stanabe!

That hard wrap code helped me with trying to adjust the output from the Fortune program. 

First I had to remove all \n characters from my literary quotes text file (used to make a Fortune .dat file), so that I would get neat end of line returns. 

Then I did find/replaces to adjusted each % to its own line, and I did the same to get the author name for each quote on its own line. 

Then I ran your code. It worked great except that it put a space before each \n return. So, when I used strfile, it just read it as one long string. Getting rid of all the trailing whitespaces with Cream sorted that out. 

Now my Fortune output in Conky is flawless. Thanks again!!!

---

