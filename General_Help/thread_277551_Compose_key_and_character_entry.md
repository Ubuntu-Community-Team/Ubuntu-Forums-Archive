---
title: "Compose key and character entry"
date: 2006-10-14
forum: General Help
---

### Post by wildutah on 2006-10-14
On my Dapper machine there is a file that pretends to list compose key combinations, but the key combinations it lists don't work.

The compose key combinations are keys that, pressed consecutively, produce input characters different from the characters (if any) that a single keypress would produce.  

The classic example is combinations like [compose]~n to produce ñ or [compose]"i to produce ï.  The compose key on your keyboard is whichever key you have mapped the Multi_Key modifier to (often people choose right-window key - you can stick a tiny cutout of a mailing label to the key to cover the unsightly Windows™ logo).  Search there forums on Multi Key to find deatils on the mapping.

Now the file **/usr/share/X11/locale/en_US.UTF-8/Compose** lists about 5000 useful ways to generate special, foreign, and unicode characters using the compose key.  but most of them don't work.  I just get a loud beep and no characters.

Examples:
[SIZE="3"][B]Compose says this    Supposedly makes   I get
[Multi_key]'i         í                   í 
[Multi_key]oo         °                --beep--
[Multi_key]oc         ©                   ©
[Multi_key]or         ®                --beep--
[Multi_key]<'         ‘                   ‘
[Multi_key]>'         ’                   ’
[Multi_key]<"         “                --beep--
[Multi_key]>"         ”                --beep--[/B][/SIZE]
(note:  Ubuntu Forums doesn't accept table tags)

Note that **/usr/bin/xev** gives the correct values for these character combinations (e.g. **XmbLookupString gives 3 bytes: (e2 80 9d) "”" **) while my various applications (gtk apps, Mozilla, others) all just beep and show no text.  I can cut and paste from xev to the other apps, so inserting the characters is possible.

Does anybody have any ideas about how I can get special characters as detailed in the Compose file?

---

