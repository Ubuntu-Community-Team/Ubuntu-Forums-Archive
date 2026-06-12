---
title: "Literate Editor with Outlines LEO"
date: 2008-02-29
forum: General Help
---

### Post by Rick Z on 2008-02-29
Does anyone knows how to install Literate Editor with Outlines LEO?  I am fairly new to linux not sure how to complie the program as it mention on the auther's website.  

[http://webpages.charter.net/edreamleo/install.html#how-to-install-leo-on-linux](http://webpages.charter.net/edreamleo/install.html#how-to-install-leo-on-linux)

Please help.

Thanks.

---

### Post by countryparson on 2008-03-11
Hi,
I'm fairly new to linux myself, but I noticed no one else had answered.  Maybe someone else can be more helpful:
This isn't a file to be compiled, but it does have to be installed manually.  The instructions from the site give you two options 1, just add the folder to your home directory and make sure its in your path or 2, you're supposed to be able to run a script to have it installed system wide.  I couldn't get the second option to work.

First: you'll need to make sure you have python-tk

```
sudo apt-get install python-tk
```

Next: if you don't already have one create a bin directory in your $HOME directory:

```
mkdir ~/bin
```

Unzip the downloaded leo file into the newly made bin folder.  Double-click the .zip file and extract it into the ~/bin folder.  

Make sure that ~/bin/leo-VERSION.NO/src/leo.py is executable (Make sure that VERSION.NO matches what you downloaded:

```
chmod +x ~/bin/leo-VERSION.NO/src/leo.py
```

Finally add a link to this file in your ~/bin directory.  You can use Nautilus to navigate to the file and right click on it.  This will open a context menu that will allow you the Make a Link.   Cut and paste the link into your ~/bin folder.  Rename the link 'leo'.

You should be able to launch it by typing leo in a terminal or press ALT+F2 and type leo there.

If it doesn't work you might need to log out and log back in for your ~/bin directory to be added to your path.

Like I said, I'm pretty new to linux myself so this is probably not the best solution, but since no one else had posted I thought I'd give you something to work with.  Hope it helps.

---

### Post by Rick Z on 2008-03-12
Thank you so much!!! I will give that a try!!!

:)

---

