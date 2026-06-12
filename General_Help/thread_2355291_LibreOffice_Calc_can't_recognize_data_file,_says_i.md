---
title: "LibreOffice Calc can't recognize data file, says it doesn't exist"
date: 2017-03-11
forum: General Help
---

### Post by steve169 on 2017-03-11
I'm running Ubuntu 16.04.02 on a Dell Inspiron 660. Windows is also installed on the same solid-state drive. A third partition on the same drive -- Drive E, formatted NTFS -- holds all my data files.

I have two shortcuts on my desktop that start LibreOffice and has it call up a data file. Here's an example:

[COLOR=#000000][IMG]/home/stevie/Pictures/Link to Screenshot from 2017-03-10 23-35-06.png[/IMG]

I click the shortcut, then get this error message:

[/COLOR][IMG] file:///home/stevie/Pictures/Screenshot%20from%202017-03-10%2023-55-14.png[/IMG]

But the file _does_ exist as specified. The data drive is mounted, and File Manager lists the file.

When I simply start Calc, then tell it to open the data file, it does.

I am utterly confused. Any help will be greatly appreciated.

---

### Post by steve169 on 2017-03-11
I solved this through trial and error.

Instead of having the shortcut start Calc and then have it call up the data file, I reversed the process, and it works.

Now the shortcut calls up the data file, which then starts Calc.

---

### Post by howefield on 2017-03-11
Please use the paperclip icon from the Reply to Thread posting window to attach images to your posting.

Right click the icon and select properties to view and check that it is pointing to the correct path ?

What is the path ?

Edit: Scrub that, you replied during the time I had this tab open, well done on solving.

---

### Post by steve169 on 2017-03-11
Duh. The above didn't solve it at all.

I finally persuaded LibreOffice Calc to call up the data file by inserting **-o <filename>** into the shortcut command.

---

### Post by vasa1 on 2017-03-11
As you may have noticed, your images of "shortcuts" didn't show up in the first post. So people have no idea about what the command is.

If you just have text, you can post that between quote tags or, if it's terminal output, you could you code tags.

---

