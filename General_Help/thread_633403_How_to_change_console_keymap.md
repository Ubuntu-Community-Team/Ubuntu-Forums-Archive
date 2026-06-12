---
title: "How to change console keymap??"
date: 2007-12-06
forum: General Help
---

### Post by dast on 2007-12-06
Can anyone enlighten me on the proper "Ubuntu way" of changing the console keymap (that is, at the console when you hit Ctrl-Alt-F1, the bare linux console, not under X11)?

The closest thing I've found is a suggestion in the following post.

[http://ubuntuforums.org/printthread.php?t=50501](http://ubuntuforums.org/printthread.php?t=50501)

The suggestion is to run the following.

sudo dpkg-reconfigure console-data

However, this does not seem to give me the option I want.  What I want specifically is to replace the Caps Lock key with Control.  I can't find any option when I reconfigure to let me do this.

I know how to change the console keymap manually with /bin/loadkeys.  I've taken a kmap.gz file, edited it by hand, and loaded it with loadkeys and I can successfully make the change on the console.  However, this is obviously lost at the next boot time.

I've got the following installed:

$dpkg --list "console*" | grep -e "^ii"
ii  console-data       2:1.02-2ubuntu4      Keymaps, fonts, charset maps, fallback table
ii  console-setup      1.16ubuntu5          Setup the font and the keyboard on the conso
ii  console-terminus   4.20-5.1             Fixed-width fonts for fast reading on the Li
ii  console-tools      1:0.2.3dbs-65ubuntu5 Linux console and font utilities
ii  consolekit         0.2.1-1ubuntu2       framework for defining and tracking users, s

And I have a /etc/console-setup/boottime.kmap.gz

It seems like running /etc/init.d/console-setup monkeys with this file, but it always seems to blow away any edits I make to boottime.kmap.gz and restore the file to the bad state of using a capslock key.

Can ANYONE please enlighten me??!?  I've been banging my head against the wall on this for hours now.

The closest thing I've gotten to making this work is editing rc.local and manually calling loadkeys.  However, I think this only works in multiuser runlevels.  I want to always load my custom keymap.  I think I could also put something in rcS.d/ and this might work better, however, these two methods obviously isn't the official "Ubuntu way" of doing things.

What is the official way to do this?

:mad:

/rant And can I just say that Ubuntu runlevel scripts are really jacked up and weird?  I miss the old days of more simple init.d scripts in much earlier versions of Debian.

---

### Post by iris-n on 2007-12-06
Well, the easiest way I see to do this is in GUI. Try System->Preferences->Keyboard
You can play with various keys dispositions there =)

---

### Post by dast on 2007-12-07
Thanks for the suggestion, but that only seems to change the setting within X (not on the raw console).  Lots of times I want to operate without X for speed reasons, or when gutsy screws up my system to the point where X doesn't work (like today).  I just can't stand caps lock keys; it must be the world's most useless key, and it takes up the spot where the control key belongs properly.  ; )

---

### Post by der_joachim on 2007-12-07
There is a nice configuration tool for such things, but you can manually edit your* /etc/defaults/console-setup* file.

Find the following lines and change them according to your preference.

```

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="dvorak"
XKBOPTIONS=""

```

Save and reboot. You.re done.

---

### Post by dast on 2007-12-07
> **der_joachim said:**
> There is a nice configuration tool for such things, but you can manually edit your* /etc/defaults/console-setup* file.  --snip--


Thanks, der_joachim.  I did finally find that file after I posted above, but I hadn't tried it yet.  I'll give it a go and see if it works.  : )

--EDIT--

It did not work for me.  I edited the XKBOPTIONS line with the same option use in xorg.conf (ctrl:nocaps if I remember right) and it did not work.  I searched for a while in /etc/init.d trying to find the script that should read this file, but I haven't found it yet.  The script that looked closest was /etc/init.d/console-setup which is run on my system in rcS.d, but I didn't find a mention of actually reading the file under defaults.

Still searching.   : /

---

### Post by buntubunny on 2008-01-07
Daniel Paul O'Donnell has an excellent post on how to do this:
[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11]("http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11")


Here's how I did it for Ubuntu Gutsy. The default "us" layout mapped my backslash ("\") key to the less-than ("<") key, so I fixed it for both X and the console (non-X).

1) I created a new X keyboard layout with the correct mappings, and enabled the layout in Ubuntu Gnome.

If you would like to see an example of the keyboard layout file, here it is:
/etc/X11/xkb/symbols/nec_e2000
```

default
partial alphanumeric_keys
xkb_symbols "nec_e2000" {
    name[Group1]= "NEC Versa E2000 Laptop Keyboard";
    include "us(basic)"

    // Alphanumeric section
    key <TLDE> { [         grave,       asciitilde ] };
    key <AE01> { [	   1,     exclam] };
    key <AE02> { [	   2,         at ] };
    key <AE03> { [	   3, numbersign ] };
    key <AE04> { [	   4,     dollar] };
    key <AE05> { [	   5,    percent,      EuroSign                   ] };
    key <AE06> { [    6, asciicircum ] };
    key <AE07> { [	   7,  ampersand ] };
    key <AE08> { [	   8,   asterisk ] };
    key <AE09> { [	   9,  parenleft ] };
    key <AE10> { [	   0, parenright ] };
    key <AE11> { [     minus, underscore ] };
    key <AE12> { [     equal,       plus ] };
    key <AB08> { [     comma,       less,      ccedilla,         Ccedilla ] };
    key <LSGT> { [ backslash,        bar                                  ] };

    include "level3(ralt_switch)"
};
```


2) Remember to update the list of keyboard layouts in /etc/X11/xkb/rules/xorg.xml and /etc/X11/xkb/xorg.lst so that X knows you added a new layout.

For xorg.xml, go to the end of the <layoutList> section, and add the following after the last </layout> tag. For me, x = nec_e2000 (must be the filename of your keyboard layout file in /etc/X11/xkb/symbols). y = a short description e.g. NEC E2000. z = a longer description e.g. NEC Versa E2000 Laptop Keyboard.

```

<layout>
  <configItem>
    <name> x </name>
    <shortDescription> y </shortDescription>
    <description> z </description>
  </configItem>
</layout>

```


For xorg.lst, add the filename of your new layout somewhere in the !layout section.

```

! layout
<---snip--->
  epo             Esperanto
  np              Nepal
  ng              Nigeria
# name of the new layout file together with short description
  nec_e2000       NEC Versa E2000
<---snip---->

```

After this, goto System->Preferences->Keyboard->Layouts and choose your layout.


Make sure that your keyboard layout works fine in Ubuntu Gnome and all the keys are correct, before proceeding to set it on the console.


3) I changed the contents of the /etc/default/console-setup file to use the new keyboard layout. console-setup (it's in /etc/init.d/console-setup) is a script that sets up the console. At bootup, you may see the message "Setting up console font and keymap", this is output by console-setup.

So here is the section in /etc/default/console-setup you need to change:
```

<---- snip ---->
# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
# changed XKBLAYOUT from "us" to "nec_e2000" - name of the keyboard symbol file
XKBLAYOUT="nec_e2000"
XKBVARIANT=""
XKBOPTIONS=""
<---- snip ---->

```

After changing this, you may need to tell console-setup to reload the keymap from your layout file. You can type this in a terminal:
```

sudo /etc/init.d/console-setup reload

```


After this, you can reboot and the keyboard layout should work in both the console and in Gnome. Appreciate your feedback on this.

---

### Post by edouardj on 2008-02-22
Hello,

i have the same problem... I must install a new keytable to work with the consoles.
With the older versions of Ubuntu (up to Dapper) it's working like a charm with:

```
install-keymap my_new_keymap
```

After a reboot the new keymap was load and even if i update my kernel.

But with fesity and gusty, impossible. Install-keymap works but only for the session in live.
I didn't test the last solution describes here but it is a very strange comportement...

Ps: i have redhat server and to configure that i must do in /etc/sysconfig/keyboard :

```
KEYTABLE=/etc/my_new_keymap
```  (very easy isn't it !)

---

### Post by edouardj on 2008-02-28
nobody?

---

