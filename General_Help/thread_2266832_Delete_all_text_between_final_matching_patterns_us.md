---
title: "Delete all text between final matching patterns using sed"
date: 2015-02-25
forum: General Help
---

### Post by CaptainMark on 2015-02-25
This is the output from the program gnu barcode 
```
[19:27:00] mark@desktop ~/Desktop $ barcode -b username -b password -e 128 -t 6x10
%!PS-Adobe-2.0
%%Creator: "barcode", libbarcode sample frontend
%%DocumentPaperSizes: a4
%%EndComments
%%EndProlog


% Printing barcode for "username", scaled  0.64, encoded using "code 128"
% The space/bar succession is represented by the following widths (space first):
% 02112141242111142121122141212412411121211244131111122141142122331112
[
%  height  xpos   ypos  width       height  xpos   ypos  width
   [57.58  10.64 772.42  1.13]      [57.58  12.25 772.42  0.49]
   [57.58  14.17 772.42  0.49]      [57.58  17.39 772.42  0.49]
   [57.58  20.28 772.42  2.42]      [57.58  23.17 772.42  0.49]
   [57.58  24.45 772.42  0.49]      [57.58  26.70 772.42  2.42]
   [57.58  29.59 772.42  0.49]      [57.58  31.52 772.42  0.49]
   [57.58  33.12 772.42  1.13]      [57.58  35.37 772.42  0.49]
   [57.58  38.58 772.42  0.49]      [57.58  40.51 772.42  0.49]
   [57.58  43.40 772.42  2.42]      [57.58  45.97 772.42  1.13]
   [57.58  49.50 772.42  0.49]      [57.58  50.78 772.42  0.49]
   [57.58  52.71 772.42  0.49]      [57.58  54.64 772.42  0.49]
   [57.58  56.24 772.42  1.13]      [57.58  60.74 772.42  2.42]
   [57.58  63.63 772.42  1.78]      [57.58  65.56 772.42  0.49]
   [57.58  66.84 772.42  0.49]      [57.58  68.45 772.42  1.13]
   [57.58  70.70 772.42  0.49]      [57.58  73.91 772.42  0.49]
   [57.58  76.15 772.42  2.42]      [57.58  79.04 772.42  0.49]
   [57.58  81.29 772.42  1.13]      [57.58  84.83 772.42  1.78]
   [57.58  86.75 772.42  0.49]      [57.58  88.36 772.42  1.13]


]    { {} forall setlinewidth moveto 0 exch rlineto stroke} bind forall
[
%   char    xpos   ypos fontsize
    [(u)   17.07 766.00  7.71]
    [(s)   21.75 766.00  0.00]
    [(e)   26.44 766.00  0.00]
    [(r)   31.13 766.00  0.00]
    [(n)   35.82 766.00  0.00]
    [(a)   40.51 766.00  0.00]
    [(m)   45.20 766.00  0.00]
    [(e)   49.89 766.00  0.00]
]   { {} forall dup 0.00 ne {
    /Helvetica findfont exch scalefont setfont
    } {pop} ifelse
    moveto show} bind forall
% End barcode for "username"


% Printing barcode for "password", scaled  0.64, encoded using "code 128"
% The space/bar succession is represented by the following widths (space first):
% 02112141112421211241142121142124211121341111212411412211323112331112
[
%  height  xpos   ypos  width       height  xpos   ypos  width
   [57.58 109.64 772.42  1.13]      [57.58 111.25 772.42  0.49]
   [57.58 113.17 772.42  0.49]      [57.58 116.39 772.42  0.49]
   [57.58 117.67 772.42  0.49]      [57.58 120.56 772.42  2.42]
   [57.58 123.45 772.42  0.49]      [57.58 125.38 772.42  0.49]
   [57.58 126.98 772.42  1.13]      [57.58 130.52 772.42  0.49]
   [57.58 132.76 772.42  2.42]      [57.58 135.65 772.42  0.49]
   [57.58 137.58 772.42  0.49]      [57.58 139.83 772.42  2.42]
   [57.58 142.72 772.42  0.49]      [57.58 145.61 772.42  2.42]
   [57.58 148.50 772.42  0.49]      [57.58 149.78 772.42  0.49]
   [57.58 151.71 772.42  0.49]      [57.58 155.24 772.42  2.42]
   [57.58 157.49 772.42  0.49]      [57.58 158.78 772.42  0.49]
   [57.58 160.70 772.42  0.49]      [57.58 163.59 772.42  2.42]
   [57.58 165.84 772.42  0.49]      [57.58 169.05 772.42  0.49]
   [57.58 171.30 772.42  1.13]      [57.58 172.91 772.42  0.49]
   [57.58 175.80 772.42  1.13]      [57.58 178.69 772.42  0.49]
   [57.58 180.29 772.42  1.13]      [57.58 183.83 772.42  1.78]
   [57.58 185.75 772.42  0.49]      [57.58 187.36 772.42  1.13]


]    { {} forall setlinewidth moveto 0 exch rlineto stroke} bind forall
[
[COLOR=#ff0000]%   char    xpos   ypos fontsize
    [(p)  116.07 766.00  7.71]
    [(a)  120.75 766.00  0.00]
    [(s)  125.44 766.00  0.00]
    [(s)  130.13 766.00  0.00]
    [(w)  134.82 766.00  0.00]
    [(o)  139.51 766.00  0.00]
    [(r)  144.20 766.00  0.00]
    [(d)  148.89 766.00  0.00][/COLOR]
]   { {} forall dup 0.00 ne {
    /Helvetica findfont exch scalefont setfont
    } {pop} ifelse
    moveto show} bind forall
% End barcode for "password"


showpage


%%Trailer

```It will allow me to print a barcode for my colleagues username and password to quickly log onto our systems at work, obviously security is not a major issue or else we wouldn't use barcodes at all but I think it goes without saying that people don't want their password printed in plain text on their keychain either so I need to remove the password text from the second barcode in the output  using a script. This text is always in the same relative place so....

By piping through sed how can I remove all the text between the final line beginning with [ and the final line beginning with ] to clarify I need to remove this part basically
```
%   char    xpos   ypos fontsize
    [(p)  116.07 766.00  7.71]
    [(a)  120.75 766.00  0.00]
    [(s)  125.44 766.00  0.00]
    [(s)  130.13 766.00  0.00]
    [(w)  134.82 766.00  0.00]
    [(o)  139.51 766.00  0.00]
    [(r)  144.20 766.00  0.00]
    [(d)  148.89 766.00  0.00]

```
I understand the basics of sed but this is way beyond my abilities.

I hope someone can help.

Many thanks
Regards
Mark

---

### Post by Lars Noodén on 2015-02-25
I'm not quite sure about which text to nuke but this removes the material between the [ ... ] blocks where [ and ] are on lines by themselves.  

```

[s]sed '/^\[$/,/^\$/{/^\]/!{/^\$/!d}}'[/s]
sed '/^\[$/,/^\]/d' 

```

Maybe if you make the text to be deleted above in red that might help.

---

### Post by CaptainMark on 2015-02-25
I've edited the post to highlight the text I want to be removed, its the text between the forth and last time [ is the first character on a line and the forth and final time ] is the first character on a line, this may be complex, it may be surprisingly easy, but I just cant grasp it.

---

### Post by steeldriver on 2015-02-25
I don't know if it's *good *sed, but assuming your file always contains exactly 2 barcodes (username and then password) you could

[LIST=1]
[*]address the lines between the first instance of '% End barcode' and the end of the file; and within that 
[*]address lines between the first instance matching 'char' and the closing ']'; and within that 
[*]delete all lines except that matching the closing ']' 
[/LIST]
 
```

sed '/^% End barcode/,$ {/char/,/^]/ {/^]/!d}}' barcode.ps > barcode_nopw.ps

```

```

$ diff barcode.ps barcode_nopw.ps
76,84d75
< %   char    xpos   ypos fontsize
<     [(p)  116.07 766.00  7.71]
<     [(a)  120.75 766.00  0.00]
<     [(s)  125.44 766.00  0.00]
<     [(s)  130.13 766.00  0.00]
<     [(w)  134.82 766.00  0.00]
<     [(o)  139.51 766.00  0.00]
<     [(r)  144.20 766.00  0.00]
<     [(d)  148.89 766.00  0.00]

```

---

### Post by Lars Noodén on 2015-02-26
I got some help from Tim over on the sed users mailing list, trying to delete the nth block of square brackets [ ... ].  There, he came up with the following:

```

sed -e '/^\[$/,/^\]$/{
    /^\[$/{
        x
        s/$/X/
        x
        t a
        :a
        }
    x
    s/^X\{4\}$/&/
    x
    T
    d
    }'

```

I see how it works but could not have come up with that myself, I think.  It keeps track of the count by adding an uppercase X in the hold space for each block, then quitting with a T.  The "t a" is needed to clear the successful pattern match flag.

It leaves everything untouched except for that last block which gets deleted.

Edit: and Davide came up with a shorter set

```

:loop
$!{
  N
  b loop
}
s/\[[^]]*\]//4

```

---

### Post by CaptainMark on 2015-02-26
@ Lars Nooden - Wow, that went completely over my head, I appreciate the effort but that just lost me.

@ steeldriver - Great this works for me, the barcodes do only contain the username and password so that will do perfectly for my needs, perhaps if you wouldn't mind could you break it down a little more to help me understand it better, I'm stuck on what /char/ references?

---

### Post by steeldriver on 2015-02-26
The 

```

/char/

```

just matches literal string *char* in the comment string - if that's not specific enough, you could do something like

```

/^%\s*char/

```

which would further restrict it, just to be a little more robust.

---

### Post by Lars Noodén on 2015-02-27
The second one is easier to follow.  It uses N to keep pushing incoming lines into the same pattern space.  Then 4 in the s///4 deletes the 4th occurance of the pattern.  N is used for multi-line matching.

The first one is more complex because it keeps swapping the contents of the hold space with the pattern space using x.  But it counts up the the number of patterns found by appending an X to the hold space every time and then if the "right" number of Xs is there.  Once the desired number is there, it skips printing that one.

---

