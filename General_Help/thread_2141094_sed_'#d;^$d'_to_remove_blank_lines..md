---
title: "sed '/*#/d;/^*$/d' to remove blank lines."
date: 2013-05-01
forum: General Help
---

### Post by epikvision on 2013-05-01
I've been using vim to do some written homework lately.  Yesterday, I encountered a good use for sed.

```
# Remove comments and blank lines.
sed '/*#/d;/^*$/d'
```

I wanted to test it out on an assignment to remove some blank lines, but I don't think it's working. Let's say my assignment was foo.txt.

```
sed '/*foo.txt/d;/^*$/d'





```

It only results in blank lines themselves until I terminate it. How can I make this work?

---

### Post by Vaphell on 2013-05-01
foo.txt is a file you want to process?
```
sed 'your expression here' foo.txt
```

---

### Post by markbl on 2013-05-01
You want to remove comments and blank lines?
```

sed -e'/^#/d' -e'/^$/d' foo.txt

```

---

### Post by epikvision on 2013-05-01
Can you explain what /^#/d means?  I get that ^$ from start to the end of a line.

---

### Post by markbl on 2013-05-01
> **epikvision said:**
> Can you explain what /^#/d means?  I get that ^$ from start to the end of a line.
Delete any line starting with a "#', i.e. a comment line.

---

### Post by Vaphell on 2013-05-02
^ and $ are start-of-line and end-of-line markers, ^$ simply means 'nothing between start and end (empty line)', while ^# means '# right at the beginning of the line'.

---

### Post by epikvision on 2013-05-02
Is there a special use for this command?  I assume it removes all bells and whistles and shows only raw code without any formatting to look at.

---

### Post by matt_symes on 2013-05-02
Hi

Personally i use this as it also strips off # comments in the middle of a line and strips spaces off the end of a line.

```
sed -e 's/#.*$//' -e 's/[ ]*$//' -e '/^$/d'
```

```
matthew-S206:/home/matthew/useful_commands_dir % cat tmp
This
#deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
is


#deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
a test #        test
matthew-S206:/home/matthew/useful_commands_dir % sed -e 's/#.*$//' -e 's/[ ]*$//' -e '/^$/d' tmp
This
is
a test
matthew-S206:/home/matthew/useful_commands_dir % 

```

EDIT: You can use a semi colon as a delimiter as well. 

Kind regards

---

### Post by epikvision on 2013-05-02
Wow, it makes things seem pretty darn clean!  Thanks for all the posts.

---

