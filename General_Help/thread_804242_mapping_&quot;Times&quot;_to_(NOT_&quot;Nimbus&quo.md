---
title: "mapping &quot;Times&quot; to (NOT &quot;Nimbus&quot;) with fontconfig"
date: 2008-05-22
forum: General Help
---

### Post by clconway on 2008-05-22
As noted on [this Launchpad bug page]("https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/41411"), fontconfig maps the font Times to "Nimbus Roman No9 L" by default, which doesn't render very well (in Firefox, at least). For everyday use, I'd very much like to map Times to the DejaVu or Liberation serif fonts. 

One way to accomplish this is apparently to remove [FONT="Courier New"]gsfonts[/FONT] and/or delete/move [FONT="Courier New"]/usr/share/fonts/type1/gsfonts[/FONT], but the number of packages that depend on Ghostscript fonts makes that seem like a seriously bad idea.

I think one should be able accomplish this by re-mapping the font in [FONT="Courier New"]~/.fonts.conf[/FONT], but I haven't been able to get it to work. Here's the file I'm using:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <alias>
    <family>Times</family>
    <prefer><family>DejaVu Serif</family></prefer>
  </alias>
</fontconfig>

```

This doesn't work at all:
```
$ sudo fc-cache
$ fc-match times
n021003l.pfb: "Nimbus Roman No9 L" "Regular"

```

Just to make sure I was modifying the right file, I tried re-mapping the Serif font:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <alias>
    <family>Times</family>
    <prefer><family>DejaVu Serif</family></prefer>
  </alias>
  <alias>
    <family>Serif</family>
    <prefer><family>Monospace</family></prefer>
  </alias>
</fontconfig>

```

This works fine:
```

$ fc-match serif
DejaVuSerif.ttf: "DejaVu Serif" "Book"
$ sudo fc-cache
$ fc-match serif
DejaVuSansMono.ttf: "DejaVu Sans Mono" "Book"
$ fc-match times
n021003l.pfb: "Nimbus Roman No9 L" "Regular"

```

I've tried moving [FONT="Courier New"]~/.fonts.conf[/FONT] to [FONT="Courier New"]/etc/fonts/conf.d/00-no-nimbus.conf[/FONT], [FONT="Courier New"]/etc/fonts/conf.d/99-no-nimbus.conf[/FONT], and [FONT="Courier New"]/etc/fonts/conf.d/no-nimbus.conf[/FONT]: all equally useless. What am I missing here?

---

### Post by incandenza on 2008-05-23
I don't know; I'm the one who suggested moving the gsfonts folder out of the way, so I'll be interested to see if you find a better answer.

I'm surprised that more people aren't bothered by this--don't they notice the terrible font rendering in Firefox on certain sites?

Moving gsfonts has not caused any problem for me, except for certain cases where the Nimbus fonts would actually look better, for example rendering certain PDFs in evince.

---

### Post by feign2 on 2008-05-23
I am not sure who to credit this to, I think it was Steve Langasek in the bug report. The following works for me:

0. backup /etc/fonts/conf.d/30-metric-aliases.conf
1. sudo gedit /etc/fonts/conf.d/30-metric-aliases.conf
2. ctrl-h, replace all
   Nimbus Roman No9 L  ->  DejaVu Serif
   Nimbus Sans L  ->  DejaVu Sans
   Nimbus Mono L  ->  DejaVu Sans Mono
3. ctrl-alt-backspace to restart X
4. fc-match Helvetica  //show actual font used

Of course this is only a temp solution as it 'breaks' the 'correct' mapping to true printer fonts. Since I never need that kind of DTP accuracy, I am OK with this.

Edit: Sorry, forgot to suggest backing up your conf file in case you want to revert.

---

### Post by clconway on 2008-05-27
feign2, Thanks a lot. Instead of modifying the aliases, I just commented out the following lines:

```

<!-- Map generics to specifics -->


	<!-- PostScript -->
        <alias binding="same">
	  <family>Helvetica</family>
	  <accept>
	  <family>Nimbus Sans L</family>
	  </accept>
	</alias>

        <alias binding="same">
	  <family>Times</family>
	  <accept>
	  <family>Nimbus Roman No9 L</family>
	  </accept>
	</alias>

        <alias binding="same">
	  <family>Courier</family>
	  <accept>
	  <family>Nimbus Mono L</family>
	  </accept>
	</alias>

```

Also, it's not necessary to restart X: running fc-cache refreshes the font aliases.

```

$ fc-cache
$ fc-match times
LiberationSerif-Regular.ttf: "Liberation Serif" "Regular"

```

Still, it seems there should be a solution that doesn't involve modifying [FONT="Courier New"]/etc/fonts/conf.d[/FONT]. Why can't I override the [FONT="Courier New"]30-metric-aliases.conf[/FONT] settings in [FONT="Courier New"]~/.fonts.conf[/FONT]?

---

### Post by incandenza on 2008-05-27
> **clconway said:**
> feign2, Thanks a lot. Instead of modifying the aliases, I just commented out the following lines:


By the way, this alternative only seems to work because you are using the Liberation fonts.  Without the Liberation fonts, commenting out that section (or both sections) still left me with Nimbus.  Changing the strings as in the original suggestion still worked.

These fixes still have the same effect for me as just moving the gsfonts directory, though; i.e. there's no way to get the Nimbus fonts for the few situations where I actually do want them (PDF rendering).  (Although I suppose there are fonts in gsfonts other than Nimbus that are used somewhere, I've never noticed them.)

---

### Post by clconway on 2008-05-27
I think maybe a better solution (and the right way to close the linked bug) is to modify the above lines to:

```

<!-- Map generics to specifics -->


	<!-- PostScript -->
       	<match target="pattern">
          <test name="family">
            <string>Helvetica</string>
          </test>
          <test name="anymetrics" qual="all" compare="not_eq">
            <bool>true</bool>
          </test>
          <edit name="family" mode="append">
            <string>Nimbus Sans L</string>
          </edit>
     	</match>

       	<match target="pattern">
          <test name="family">
            <string>Times</string>
          </test>
          <test name="anymetrics" qual="all" compare="not_eq">
            <bool>true</bool>
          </test>
          <edit name="family" mode="append">
            <string>Nimbus Roman No9 L</string>
          </edit>
     	</match>

       	<match target="pattern">
          <test name="family">
            <string>Courier</string>
          </test>
          <test name="anymetrics" qual="all" compare="not_eq">
            <bool>true</bool>
          </test>
          <edit name="family" mode="append">
            <string>Nimbus Mono L</string>
          </edit>
     	</match>

```

This preserves the Postscript -> Nimbus font aliases in the case where metric-compatibility is desired and suppresses them when it isn't (i.e., anymetrics=true). This gets me:

```

$ fc-match times
LiberationSerif-Regular.ttf: "Liberation Serif" "Regular"

```

Now, since the Liberation Serif font is actually too small on my screen (a DPI issue?), I prefer the DejaVu Serif font when metrics aren't an issue. So I added the following to [FONT="Courier New"]~/.fonts.conf[/FONT]:

```

  <match target="pattern">
    <test name="family">
      <string>Times</string>
    </test>
    <test name="anymetrics" qual="all" compare="eq">
      <bool>true</bool>
    </test>
    <edit name="family" mode="assign">
      <string>DejaVu Serif</string>
    </edit>
  </match>

```

And:
```

$ fc-match times
DejaVuSerif.ttf: "DejaVu Serif" "Book"

```

This seems to be exactly what I want.

---

### Post by clconway on 2008-05-27
> By the way, this alternative only seems to work because you are using the Liberation fonts. Without the Liberation fonts, commenting out that section (or both sections) still left me with Nimbus. Changing the strings as in the original suggestion still worked.

Although I prefer the DejaVu fonts to the Liberation fonts for screen-reading, it makes sense to have a metric-compatible set of alternatives installed, IMHO.

---

### Post by incandenza on 2008-05-27
EDIT: Oops, never mind, I overlooked the second part of your fix.  Yeah, this looks good now.

---

### Post by rbprogrammer on 2008-05-27
Not sure if this might help you, but did you check out in synaptic the package called: msttcorefonts ?

The package is full of the common fonts used.  Times New Roman, Courier New, etc...

---

### Post by incandenza on 2008-05-27
Hmm, actually I'm still having trouble here.  I did the same thing in my .fonts.conf as you did, except I did all three fonts (Times, Helvetica, Courier), because I don't want to see Liberation in Firefox.

But yet, I get Liberation in Firefox anyway.  And what's more, I start getting DejaVu in evince, which should be asking for the metric version.

In fact, there seems to be something strange here, because if I reverse the comparison from "eq" to "not_eq" in the .fonts.conf, it matches anyway.  Maybe if the 'anymetrics' key doesn't exist the test is skipped or something?

---

### Post by clconway on 2008-05-27
> Not sure if this might help you, but did you check out in synaptic the package called: msttcorefonts ?

Setting aside licensing/freedom issues, the MS fonts don't render as well as Liberation/DejaVu with subpixel smoothing turned on.

---

### Post by clconway on 2008-05-27
> **incandenza said:**
> Hmm, actually I'm still having trouble here.  I did the same thing in my .fonts.conf as you did, except I did all three fonts (Times, Helvetica, Courier), because I don't want to see Liberation in Firefox.

But yet, I get Liberation in Firefox anyway.  And what's more, I start getting DejaVu in evince, which should be asking for the metric version.

In fact, there seems to be something strange here, because if I reverse the comparison from "eq" to "not_eq" in the .fonts.conf, it matches anyway.  Maybe if the 'anymetrics' key doesn't exist the test is skipped or something?

You may need to add rules for "Times New Roman", "Arial", and "Courier New" as well, if you *never* want to see Liberation fonts in Firefox. Setting/not setting anymetrics properly may be a firefox and/or evince bug...

---

### Post by incandenza on 2008-05-27
> **clconway said:**
> You may need to add rules for "Times New Roman", "Arial", and "Courier New" as well, if you *never* want to see Liberation fonts in Firefox. Setting/not setting anymetrics properly may be a firefox and/or evince bug...

Hmm, well, I went all through this with FC_DEBUG trying to figure out what was going on.

For one thing, neither Firefox nor evince ever sets the 'anymetrics' flag that I can see.  Because of the qual="all" tag on the 'anymetrics' test, if the anymetrics flag does not exist the condition always evaluates to true, whether you are comparing against true or false (because 'all' of the values for anymetrics, of which there are none, evaluate to anything).  So I don't think these tests mean what they're supposed to.

In fact, I don't really see how you can do a proper test against a possibly-missing key with this "qual" tag.  qual="any" always gives false for any condition if the tag is missing, and qual="all" always gives true.

The only reason the test on anymetrics does anything, as far as I can tell, is that it changes the reference to Nimbus from 'strong' to 'weak', which gives it less precedence.  It's almost the same as just commenting it out.

Anyway, it doesn't matter, because without the anymetrics key set there's no way to distinguish the context anyway.  I wound up just putting strong bindings directly for DejaVu from Helvetica, Times, and Courier in my fonts.conf, and removing Liberation.  I guess if I want evince to work properly, I'll move my .fonts.conf temporarily out of the way before running it.

At least I figured out how to get what I want using just the .fonts.conf and not having to edit /etc/fonts.

EDIT: Also, I don't think your .fonts.conf actually overrides Liberation in Firefox--are you sure that it does?  At least, that does not seem to be possible here.  The way Firefox asks for the font is different than what 'fc-match' does, and the weak binding in the .fonts.conf doesn't seem to be able to override the strong one for Liberation.

---

### Post by clconway on 2008-05-27
incandenza, You're right. With
```

  <match target="pattern">
    <test name="family">
      <string>Times</string>
    </test>
    <test name="anymetrics" qual="all" compare="eq">
      <bool>true</bool>
    </test>
    <edit name="family" mode="assign">
      <string>DejaVu Serif</string>
    </edit>
  </match>

```
or with
```

  <match target="pattern">
    <test name="family">
      <string>Times</string>
    </test>
    <edit name="family" mode="assign">
      <string>DejaVu Serif</string>
    </edit>
  </match>

```
in [FONT="Courier New"]~/.fonts.conf[/FONT], I get DejaVu Serif in Firefox. With
```

    <test name="anymetrics" qual="any" compare="eq">
      <bool>true</bool>
    </test>

```
I get Liberation Serif.

There are several separate issues here:
[LIST=1]
[*]The Nimbus fonts render poorly. This is probably due to a lack of hinting support in legacy Postscript fonts.
[*]The Nimbus and Liberation fonts are too small by default, effectively much smaller than DejaVu at the same nominal point size (see attached).
[*]Fontconfig has buggy anymetrics support and/or Fontconfig clients don't consistently provide appropriate anymetrics parameters
[/LIST]
Unfortunately, the Nimbus and Liberation fonts seem to be the only metric-compatible replacements for the standard Postscript and Microsoft fonts that are used in many web, PS, and PDF documents, so replacing them with DejaVu fonts universally isn't a good option.

---

### Post by incandenza on 2008-05-27
> **clconway said:**
> 
Unfortunately, the Nimbus and Liberation fonts seem to be the only metric-compatible replacements for the standard Postscript and Microsoft fonts that are used in many web, PS, and PDF documents, so replacing them with DejaVu fonts universally isn't a good option.

True, it is not really a "good" solution, but it is the best available solution I have at the moment, unless someone can explain to me how to do something better.  Switching from Nimbus to Liberation is not a real improvement for me, but just a sideways shift.

I suppose I could just give up and use the msttcorefonts, but I'm not too thrilled about that either.

The thing is, for some reason this worked fine under Gutsy; Firefox never used the Nimbus fonts there.  I tried to figure out what changed, even copying my old /etc/fonts directory over, but I could never make it work the same since Hardy.

EDIT: Actually I suspect there is some bug in the fontconfig code itself that causes a slight change in behavior between the Gutsy version and the Hardy version, even with the same config files.  Problem is, this whole system is so nightmarishly complex that I doubt many people fully understand what it's supposed to be doing, much less are able to identify a minor change in behavior.  If you try to follow through even the choice of a single font through these FC_DEBUG printouts, it's just ridiculous.

---

### Post by clconway on 2008-05-27
I came up with an unrelated fix that might be better:
raise the DPI setting in System -> Preferences -> Appearance -> Fonts -> Details and turn on autohinting with ```
sudo ln -s /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d
``` This drastically improves the rendering of the Nimbus and Liberation fonts. They're still too small in Firefox, but at least they aren't hideous to behold.

---

### Post by m-y-t-h-o-s on 2008-08-09
So, when i understand it right, we want to change the Nimbus and Liberation-family to Dejavu (or Bitstream in my case) only for Firefox. I solved it that way:

1) cp /etc/fonts/fonts.conf /etc/fonts/fonts.conf.firefox
2) append the whole configuration on the end of /etc/fonts/config.avail/30-metric-aliases.conf to the new fonts.conf.firefox. that means all between <fontconfig> </fontconfig>.
3) replace in fonts.conf.firefox all 
Nimbus Roman No9 L and Liberation Serif to DejaVu Serif or Bitstream Vera Serif
Nimbus Sans L and Liberation Sans to DejaVu Sans or Bitstream Vera Sans
Nimbus Mono L and Liberation Mono to DejaVu Sans Mono or Bitstream Vera Sans Mono
4) edit /usr/bin/firefox and append under #!/bin/sh the row
'export FONTCONFIG_FILE=/etc/fonts/fonts.conf.firefox' (without ')
5) restart firefox

thats it =)

---

### Post by incandenza on 2008-10-04
A belated thanks for that last tip.  I wasn't aware of the FONTCONFIG_FILE variable.  Now I can change the fonts the way I like just for Firefox, and leave everything else alone.

Thanks!

---

