---
title: "How can i crop a part of a text file?"
date: 2008-04-10
forum: General Help
---

### Post by Simstud on 2008-04-10
I want to do something that seems fairly easy, but I can't seem to make it work. My work posts a weekly schedule online. I want to take that information and display it in conky.

  So I can download the website using httrack:
```
httrack --path /dir/to/save/in --get http://website/to/copy.html
```
  and now I want to search the html file for certain tags and get everything that falls between them. Cat and grep treat the file as if everything were on one line. I could use cut if I could tell what character positions the information I want is at. I tried using sed but it always returns the original file. I think it's treating the entire file as one long string, and it can't handle a string that long. Maybe. Any other ideas?

---

### Post by fguilhon on 2008-04-10
You are seeing things in one line because they probably are.
There are a lot of PHP (or similar) programmers out there that do not care about the format of the final HTML.
So, you have to take a look at the **sed** (it's complex, look for a tutorial in google) command. I'm not a sed wizard and right now and in a hurry... So I can't help right now I'll reply to you later with any findings..
good luck..

---

### Post by stylishpants on 2008-04-10
You might have better luck using lynx to get the file, it would preserve the newlines.

```

# Get the web page as formatted text
lynx -dump http://website/to/copy.html > /dir/to/save/in/filename.txt

# Get the web page as raw HTML
lynx -source http://website/to/copy.html > /dir/to/save/in/filename.html


```


If you want help with the actual parsing, then post some examples of what the input file looks like and what you want to see in the output.

---

### Post by Simstud on 2008-04-14
Thanks for the ideas.

The html file I want is in the form:
<html>
yadda yadda
<table bgcolor="#CCCCCC"> the html code I want to cut </table>
more yadda yadda
</html>

Lynx is also giving me a single line file. But if I could search it for "<table bgcolor="#CCCCCC">" and get the position of the first character, I could use cut to get the data I want. Is there any way to do that?

If real data helps, the page I want is [http://bama.ua.edu/~chem/index.shtml](http://bama.ua.edu/~chem/index.shtml)

Thanks.

---

### Post by stylishpants on 2008-04-17
It's a line endings problem.  That page uses CR line endings for some reason, instead of CRLF or just LF.  ([http://en.wikipedia.org/wiki/Newline](http://en.wikipedia.org/wiki/Newline) if you don't know what I'm talking about.)

So, you have to replace the CR line endings  with LF, and then the standard line-oriented tools like grep will work..

```

# get the HTML file and fix the line endings
links --source http://bama.ua.edu/~chem/index.shtml  | sed 's/\r/\n/g' > file.html

# cut out the table
cat file.html | sed -n '/<table .*bgcolor="#CCCCCC">/,/<\/table>/p'


```

You could also put it all together on one line.

---

### Post by ghostdog74 on 2008-04-17
```

#!/bin/bash
awk '/<table bgcolor=\"#CCCCCC\">/ ,/<\/table>/{
   gsub(/<table bgcolor=\"#CCCCCC\">|<\/table>.*/,"")
   print    
}' file

```

---

### Post by ghostdog74 on 2008-04-17
> **stylishpants said:**
> 

# cut out the table
cat file.html | sed -n '/<table .*bgcolor="#CCCCCC">/,/<\/table>/p'

[/CODE]

cat is useless here.
```

sed -n '/<table .*bgcolor="#CCCCCC">/,/<\/table>/p' htmlfile

```

---

### Post by Simstud on 2008-04-25
Thanks a million everybody. I got it working. I attached the very messy script I wrote in case anyone wants to see it. I plan on cleaning it up later. I set up cron to run it every 6 hours, so I guess it doesn't have to be all that neat.

Again, thanks a lot.

---

### Post by ghostdog74 on 2008-04-26
yes, its indeed quite messy. No offense.

---

