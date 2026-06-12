---
title: "Help with sed command please ?!"
date: 2015-12-18
forum: General Help
---

### Post by fairbird on 2015-12-18
any body can help me and give advice how to fix my scripts ?!

I try to use my script to remove some lines from other file but never changed any things and no error give me ...

I don't know where is the problem :confused:

Files in attach to test ...

Thank you ...

---

### Post by TheFu on 2015-12-18
Didn't look at the attachments.
To remove lines from a file, I use **grep -v** as a filter.

---

### Post by fairbird on 2015-12-18
Thank you for replay ...

here some command line from file attach .. what your advice ?! How can i add **grep -v **with this command ?!

```
sed -i 's/\(name="list".*\)font="[a-zA-Z_]*; [0-9]*"/\1/' $SkinName
```

I want to remove all (font="") from all line have (name="list")

---

### Post by mcgess on 2015-12-19
Hi

Looking at your sample file skin-Test.txt I cant see any line matching
```
sed -i 's/\(name="list".*\)font="[a-zA-Z_]*; [0-9]*"/\1/' $SkinName

```

There is one that matches
```
sed -i 's/\(name="list".*\)font="[a-zA-Z_]*;[0-9]*"/\1/' $SkinName

```

---

### Post by fairbird on 2015-12-19
@[**[COLOR=#000000]mcgess[/COLOR]**]("http://ubuntuforums.org/member.php?u=956340")
Yes ..
Thank you very much ...
You are right ...

Solved

---

### Post by fairbird on 2015-12-19
One more question please ...

If i have two lines like these 

<widget name="listbox"  position="20,20" size="1180,681" itemHeights="113,68,34" fontSizesOriginal="20,24" >
<widget name="list"  position="50,100" size="55,70" itemHeights="113,68,34" fontSizesOriginal="30,26,26" >

And I want to remove all (fontSizesOriginal=" ") from all lines how to use sed command ?!

Thank you

---

### Post by steeldriver on 2015-12-19
I'd probably do something like

```

sed '/<widget name.*>/ s/fontSizesOriginal=["][^"]*["]//' file

```

---

### Post by fairbird on 2015-12-19
Thank you ...
But i want command without (<widget name.*>) some lines come like this 
<screen name="listbox"  position="20,20" size="1180,681" itemHeights="113,68,34" fontSizesOriginal="20,24" >

so what is your advice ?!

Thank you

---

### Post by steeldriver on 2015-12-19
```

sed 's/fontSizesOriginal=["][^"]*["]//' file

```

will remove a single instance of

```

fontSizesOriginal="*anything between doublequotes*"

```

in any line

---

### Post by fairbird on 2015-12-19
Ok...
I use this command

sed -i 's/fontSizesOriginal=["][^"]*["]//' file

Thank you very much

---

### Post by TheFu on 2015-12-19
Glad you got it solved. sed is a quick tool for stuff like this.

Whenever a non-trivial regex is necessary for a solution, I switch to perl which is THE TOOL (IMHO) for this stuff. However, python, ruby, go, ... are all excellent alternate choices.  Why?  Pattern grouping, extended pattern matching, the ability to comment regex when they are multiline, and just the nature of a complete programming language for non-trivial stuff. Perl has regex macros to make patterns easier to match too - like :digit: or :alpha: - plus Perl handles unicode characters as expected ... so when a digit is in a different, non-ascii, character set, it is still known to be a digit.  After all, every language has 0-9 in their own characters, but comparing [0-9] won't match on any of the unicode versions outside normal ASCII.  [http://perldoc.perl.org/perlreref.html#CHARACTER-CLASSES](http://perldoc.perl.org/perlreref.html#CHARACTER-CLASSES)

I'd probably use 
sed -i  \
-e 's|font[.]*=["][^"]*["]||gi' \
$file

That way the regex would be compiled only once and match case insensitively. Also, by using the pipe (|) as a separator, the '/' that could show up in HTML won't be an issue. I haven't dealt with HTML seriously in many years, so I'm a little rusty on what is and isn't allowed where.  For the last few years, tend to use a templating engine to generate what the clients get to see anyway.  Plus, most the interfaces we create are xml, json enabled - just ask for those instead to get the data without the HTML stuff.

---

### Post by fairbird on 2015-12-20
@[**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685")
Thank you :)

---

