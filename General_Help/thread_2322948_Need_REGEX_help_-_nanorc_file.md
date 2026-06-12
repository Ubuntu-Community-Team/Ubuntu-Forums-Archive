---
title: "Need REGEX help - nanorc file"
date: 2016-05-01
forum: General Help
---

### Post by Krupski on 2016-05-01
Hi all,

I'm trying to make an RC file for the nano editor to "syntax" highlight Intel HEX files (the kind a compiler generates for loading into a microcontroller).

What I want is something like this:

[SIZE=2][B][COLOR=#008000]:[/COLOR][COLOR=#0000cd]10[/COLOR][COLOR=#b22222]0230[/COLOR][COLOR=#006400]00[/COLOR][COLOR=#ff0000]A109B109C1F7ABBFFC01879196910196[/COLOR][COLOR=#ff8c00]65
[/COLOR][/B]

This breaks down into:

**[COLOR=#008000]: [/COLOR]**(start marker)
**[COLOR=#0000cd]10 [/COLOR]**(data length)
**[COLOR=#b22222]0230 [/COLOR]**(address)[B][COLOR=#006400]
00 [/COLOR][/B](record type)[B][COLOR=#ff0000]
A109B109C1F7ABBFFC01879196910196 [/COLOR][/B](16 bytes actual data)
**[COLOR=#ff8c00]65 [/COLOR]**(checksum)[/SIZE]

n[SIZE=4]**[COLOR=#ff8c00][/COLOR]**[/SIZE]ot those exact colors of course, but I want to highlight the data length, address, record type, the data itself and the checksum[SIZE=4]**[COLOR=#ff8c00][/COLOR]**[/SIZE].

I can't seem to figure out how to skip a part, then highlight a part, then skip the rest... the best I can seem to manage is (using "start=" and "end=") just two different colors.

Any nano and regex guru able to help me? I'd really appreciate it!

[SIZE=4][B][COLOR=#ff8c00]
[/COLOR][/B][/SIZE]

---

### Post by BasiliusCarver on 2016-05-02
I'm not a nano guru (emacs ftw) but I use regex daily so I had a crack at this.

The nano rc format is a bit interesting...
Looking at the example files they're laid out so that they highlight the largest matches first and then cascade down to smaller matches.
The highlighting is positional based on character index and these intel files start with the colon character so this will only work for these files.

If you're curious about how the regex works regex101.com is awesome for validating this stuff.
[Regex101 nanorc hex example]("https://www.regex101.com/r/cR4zU9/1")

**Actual nanorc file:**
```
## Intel HEX regex for nano - fix this extension to whatever your files are using
syntax "hex" "\.hex$"

##
## The order of	the following rules is important because they are cascading.
## Where the regex is yuck I have put the target colored group	in parentheses ().
##

## Data
## This is the majority of the input so apply to the whole line
color red        "^(.+)$"

## Checksum
## The last byte of each line
color yellow  	 "[A-Z0-9]{2}$"

## Record type
## The fourth byte
color green       "^:[A-Z0-9]{6}([A-Z0-9]{2})"

## Address
## The second and third bytes
color magenta     "^:[A-Z0-9]{2}([A-Z0-9]{4})"

## Data length
## The first byte
color blue        "^:([A-Z0-9]{2})"

## Start marker
color green       "^:"

## Apply the EOF syntax	last
color white,black "FF$"

```

---

### Post by Krupski on 2016-05-02
> **beatbophiphop@gmail.com said:**
> I'm not a nano guru (emacs ftw) but I use regex daily so I had a crack at this.

The nano rc format is a bit interesting...
Looking at the example files they're laid out so that they highlight the largest matches first and then cascade down to smaller matches.
The highlighting is positional based on character index and these intel files start with the colon character so this will only work for these files.

If you're curious about how the regex works regex101.com is awesome for validating this stuff.
[Regex101 nanorc hex example]("https://www.regex101.com/r/cR4zU9/1")



Holy smokes! It's EXACTLY what I was looking for!  [img]http://www.hobbytent.com/images/smilies/the-man.gif[/img]

By the way, I had been using a similar regex online live site ( [http://regexr.com/](http://regexr.com/) ) but the one you linked to for me seems to be more comprehensive. I'll have to try it.

Thanks SO MUCH for the quick and perfect reply!!

-- Roger

(edit to add): I tweaked the colors a bit... but as you can see it's working perfectly. And, highlighting the end of file "0xFF" was a nice plus... I never thought of that when I was trying to make it work.

Thanks again!!

---

### Post by BasiliusCarver on 2016-05-02
Awesome. Glad I could help.

---

