---
title: "How do i map a key like this?"
date: 2008-01-10
forum: General Help
---

### Post by schmolch on 2008-01-10
Im trying to map a key to Ctrl+Right and a second key to Ctrl+Left.
I have the keycodes of those 2 keys and i can map them to any other with xmodmap, but i cannot map them to a key-combo like ctrl+right.

How can i do this please?

Thx.

---

### Post by Tenken on 2008-01-10
If you use Gnome you can go to System->Preferences->Keyboard shortcuts and see if what you want to map the keys to (Volume Up/Down, etc) are available options.

---

### Post by schmolch on 2008-01-10
What???

I want to map 2 keys to ctrl+right and ctrl+left, i dont see how your answer is of any relevance to that.

---

### Post by xc3RnbFO8P on 2008-01-10
You can look at this:

[http://reachbeyondgrasp.blogspot.com/2007/06/10-tips-to-customise-you-new-ubuntu.html]("http://reachbeyondgrasp.blogspot.com/2007/06/10-tips-to-customise-you-new-ubuntu.html")

---

### Post by Icebear on 2008-01-10
Hi this a guide which I wrote for myself for normal keys but it might be a help for you

go to X11/symbols diretory, 	by typing cd /etc/X11/xkb/symbols
then find layout you want to change

for example ru (for Russian)

make a backup of the selected file,	sudo cp ru ru_backup
then load the file up to edit,	sudo gedit ru

find the section you want in it to change 
in my case the phonetic layout

then swap changes you wish to make

for example: from
key	<LatV> {	[    Cyrillic_zhe,    Cyrillic_ZHE	]	};
to
key	<LatV> {	[    Cyrillic_ve,    Cyrillic_VE	]	};

If you want to add a  2nd letter to a key then at the spot where it describes the level

in the Russian phonetic spot change the level from ALPHABETIC to FOUR_LEVEL_ALPHABET or  FOUR_LEVEL

for example from
key.type[group1]="ALPHABETIC";
to
key.type[group1]="FOUR_LEVEL_ALPHABETIC";

and at the key add the letter you want to change after the first two settings.

You can use unicode numbers also instead of names. (Don't use the +  sighn  ie. U4C7)

from
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN	]	};
to
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN,	U04C8,		U4C7	]	};

then save

Then go System>preferences>Keyboard

then click layout options 
then choose third level choosers
and choose button you wish to use for the 2 
To get the 2 letter while typing hold down the 3rd level key plus the key you want to use and for capital hold shift as well

next time you log in it should work
It would be most likely best not to experiment on the default language until you tried your changes on a second language keyboard.

---

