---
title: "Using sed to mass edit html files"
date: 2013-03-06
forum: General Help
---

### Post by astarmathsandphysics on 2013-03-06
I have about 6000 html files spread over many directories, all maths and physics notes for my website.
I have external links in the footer of each page cos I think google is penalising me.
I want to replace the string

<P ALIGN=CENTER STYLE="margin-bottom: 0cm"><A HREF="http://www.studentforums.biz/">Student Forum</A> <A HREF="http://www.tutoragency.org/">Tutor Agency</A>

with

<P ALIGN=CENTER STYLE="margin-bottom: 0cm"><A HREF="http://www.studentforums.biz/" rel="nofollow">Student Forum</A> <A HREF="http://www.tutoragency.org/" rel="nofollow">Tutor Agency</A>

How do I do this with sed?
I have tried for a few hours but sed is frankly playing mozart with syntax.

---

### Post by The Cog on 2013-03-06
Try this :

Make a function that fixes a file by copy/pasting this into your command prompt:
```
function fixfile {
echo fixing file $1
sed -i \
-e 's_<A HREF="http://www.studentforums.biz/">_<A HREF="http://www.studentforums.biz/" rel="nofollow">_g' \
-e 's_<A HREF="http://www.tutoragency.org/">_<A HREF="http://www.tutoragency.org/" rel="nofollow">_g' $1
}


```
Then try it on one file:
```
fixfile *filename*
```
and if it has the desired effect, do it on all the files:
```
find . -name '*.html' -exec fixfile '{}' \;
```
**P.S.**
Notice that I am searching for every instance of references to those two sites, not just the margin-bottom ones. That was to keep the search/replace strings short in this reply. If you need to be more specific, you can make the search/replace strings longer.

---

### Post by astarmathsandphysics on 2013-03-06
seems to be working.
A valuable piece of code

How do I edit the code to search subdirectories?

---

### Post by evilsoup on 2013-03-06
By default, that find line should search subdirectories.

---

### Post by astarmathsandphysics on 2013-03-06
When I try to edit all the files in a directory I get the error message 

find: &#8216;fixfile&#8217;: No such file or directory

---

### Post by schragge on 2013-03-06
First, export the function to subshells, then invoke a subshell in the *-exec* action of *find*.
```

export -f fixfile
find . -name \*.html -exec bash -c 'fixfile $0' {} \;

```

---

### Post by astarmathsandphysics on 2013-03-06
Whey - hey
Brilliant!

---

### Post by The Cog on 2013-03-06
Thanks, schragge. I overlooked that little complexity, and was really struggling to figure out how to do it. I still can't figure out how to do files with spaces in their names though.

---

### Post by schragge on 2013-03-06
> **The Cog said:**
> I still can't figure out how to do files with spaces in their names though.Quote it.

This
```

function fixfile {
echo fixing file $1
sed -i \
-e 's_<A HREF="http://www.studentforums.biz/">_<A HREF="http://www.studentforums.biz/" rel="nofollow">_g' \
-e 's_<A HREF="http://www.tutoragency.org/">_<A HREF="http://www.tutoragency.org/" rel="nofollow">_g' [COLOR=red]"[/COLOR]$1[COLOR=red]"[/COLOR]
}

```
and this
```

find -name \*.html -exec bash -c 'fixfile [COLOR=red]"[/COLOR]$0[COLOR=red]"[/COLOR]' {} \;

```

---

### Post by The Cog on 2013-03-06
Well, that's stupid of me. I spent an age messing around with the quoting on the find command, but never thought to go back and quote the fixfile function. Doh!

---

### Post by AexbYRB on 2013-07-31
I want to insert favicons into all my html pages to make it easy to locate my pages in tabbed browsers.
When I try this 

function fixfile {
echo fixing file $1
sed -i \
-e 's_<HEAD>_<HEAD><link rel="shortcut icon" href="/favicon.ico" type="image/png">
<link rel="shortcut icon" type="image/ico" href="http://www.astarmathsandphysics.com/favicon.ico" />_g' \
-e 's_<A HREF="http://www.tutoragency.org/" rel="nofollow">Tutor Agency</A></P>_<A HREF="http://www.tutoragency.org/" rel="nofollow">Tutor Agency</A></P>_g' $1
}




export -f fixfile
find . -name \*.html -exec bash -c 'fixfile $0' {} \;

I get the error message
 fixing file ./o_level_physics_notes/o_level_physics_notes_a_fishs_view_of_the_world.html
sed: -e expression #1, char 78: unterminated `s' command

---

