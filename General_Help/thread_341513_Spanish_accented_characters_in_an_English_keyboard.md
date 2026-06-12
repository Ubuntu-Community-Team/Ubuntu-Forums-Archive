---
title: "Spanish accented characters in an English keyboard (Xubuntu)?"
date: 2007-01-18
forum: General Help
---

### Post by joseantmm on 2007-01-18
Hello.

My IBM Thinkpad T23 has an English keyboard but I need to type accented Spanish characters. I don't want to change the configuration to a Spanish keyboard because it is too different. I want to keep the English keyboard but be able to change how some keys behave when pressed with Right Alt. 

I knew how to configure this in Windows but I am lost in Xubuntu. I have now spent a few weeks trying every app in Synaptic and following several instructions found through Google but have achieve nothing. None of the changes I have tried seem to get implemented. Help will be highly appreciated. In case it is of any interest, I post my xorg.conf details, though I guess there are other issues involved:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"thinkpad"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

---

### Post by joseantmm on 2007-01-23
Nobody here? I'll post some more info, in case it helps:

I think there is some other program interfering. When I do an $ sudo setxkbmap -layout, my xorg.conf file changes to Sundeadkeys. 

Here is the latest xorg.conf file info I'm trying, still without results:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"thinkpad"
	Option		"XkbLayout"	"es"
	Option		"XkbVariant"	"sundeadkeys"
	Option		"XkbOptions"	"lv3:ralt_switch"

---

### Post by ingeticom on 2007-04-15
Try this:

        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
        Option          "XkbVariant"    "alt-intl"

---

### Post by Icebear on 2007-04-15
How to map a keyboard in ubuntu 6.10

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

