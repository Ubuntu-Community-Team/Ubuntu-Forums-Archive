---
title: "Printing to lp"
date: 2008-05-15
forum: General Help
---

### Post by TMC on 2008-05-15
I'm trying to print from xtrkcad but the only options I get are to print to file or to print to lp.  How do I set up so that choosing lp prints to my default printer on Hardy?

Many thanks,

David Shaw

---

### Post by pointone on 2008-05-15
Printing with lp always uses the default printer, unless otherwise specified, as far as I know.

---

### Post by TMC on 2008-05-15
Well it doesn't on my system - it doesn't print to anything :-(

Any ideas?  Is it my system or xtrkcad?  Is there anything I can do to find out what's going on and fix it?

---

### Post by pointone on 2008-05-16
You can try just testing lp from the command line:

Run the "lp" command; the cursor should drop down a line. Here, you can type a message that you want printed. Press Ctrl+D when done and it should print to your default printer. If not, the problem is with your printer configuration. If it does print, the problem lies more likely with XTrkCAD.

---

### Post by TMC on 2008-05-16
Many thanks - that works fine, so I'll just take this back to the xtrkcad group  :-)

---

### Post by pointone on 2008-05-16
Something to try would be to test print to file and see if that works at all. If so, try passing the file manually to lp and see if it prints as intended.

---

### Post by TMC on 2008-05-16
It generates the PS file OK, but it won't print with lp < /proc/8770/cwd/XTC_print_test - the file goes into the print queue, but the status quickly changes to 'stopped'.

I have been given a method to get xtrkcad to 'see' my printer which works - but it still won't print (although it does print a test page OK).

I'm using an HP OJ6310 all-in-one printer which I have no problems printing to from any other program.

---

