---
title: "getting grep to do what I want."
date: 2007-08-21
forum: General Help
---

### Post by kofkof_00 on 2007-08-21
Hello,

I almost never post on a forum, but i'm at my wits end.

After a bit of web research, i've come to the conclusion that I need to use a tool called "grep" and a "regular expression" to extract the information i want from a text file.

This text file has some url's scattered inside of it. I'm trying to get grep to scan it, and output the resulting list of urls to a different text file.

I have found examples of this expression on [http://regexlib.com](http://regexlib.com)

My attempt consists of this:  grep -i -o (?<http>(http:[/][/]|[www.)(](www.)()[a-z]|[A-Z]|[0-9]|[/.]|[~])*) index.txt > justurls.txt

I don't think I need the -i, and I would like it if I could get ANY url copied to the justurls.txt, be it one that has www in it or not. (ie [http://www.anysite.com](http://www.anysite.com) and [http://anysite.com](http://anysite.com))

It's a moot point as this command only returns "bash: syntax error near unexpected token `('" at the present time.  :( What am I doing wrong? Is grep even what I should use to do this?

---

### Post by maldojr88 on 2007-08-21
yes mister...grep is what u need sir....just dont have the time to look at every detail...just be carefuck with ur notation...and make sure u have as many left parentesis or brackets as right ones.

---

### Post by jfinkels on 2007-08-21
> **kofkof_00 said:**
> Hello,

I almost never post on a forum, but i'm at my wits end.

After a bit of web research, i've come to the conclusion that I need to use a tool called "grep" and a "regular expression" to extract the information i want from a text file.

This text file has some url's scattered inside of it. I'm trying to get grep to scan it, and output the resulting list of urls to a different text file.

I have found examples of this expression on [http://regexlib.com](http://regexlib.com)

My attempt consists of this:  grep -i -o (?<http>(http:[/][/]|[www.)(](www.)()[a-z]|[A-Z]|[0-9]|[/.]|[~])*) index.txt > justurls.txt

I don't think I need the -i, and I would like it if I could get ANY url copied to the justurls.txt, be it one that has www in it or not. (ie [http://www.anysite.com](http://www.anysite.com) and [http://anysite.com](http://anysite.com))

It's a moot point as this command only returns "bash: syntax error near unexpected token `('" at the present time.  :( What am I doing wrong? Is grep even what I should use to do this?

A syntax error means that your regular expression is not in the correct form for a regular expression. I think to match an expression, you need to do:```
grep -e "*regex"*
```where *regex* is the regular expression.

I suggest starting with a small file with a few URLs so that you can test simpler regexes, and then work your way up.

Try this, friend:
```

grep -i "http[s]*://\(www\)*\..*\.com[/]*" index > justurls
```

To clarify:```

http[s]*://
```means match a string containing 'http', followed by 0 or more 's's, followed by '://'.
```
\(www\)*
```means match 0 or more sets of 'www'.
```
\..*\.
```means match a dot followed by anything followed by another dot.
```
com[/]*
```means that it ends in 'com' and 0 or more slashes.

---

### Post by daveshields on 2007-08-21
Google is our friend. A search on "regular expression to parse url" led to the post "RegEx to Match a URL" [http://www.forta.com/blog/index.cfm?mode=entry&entry=A61B9FF5-3048-80A9-EF09C0A7F1E9FBD3](http://www.forta.com/blog/index.cfm?mode=entry&entry=A61B9FF5-3048-80A9-EF09C0A7F1E9FBD3)

I can't assert this is right. But if you search around and find two folks agreeing in the same solution that may give you more confidence.

You need the "-i" to ignore the case. This is right since the case used in a URL doesn't matter. For example, [http://UBUNTU.COM](http://UBUNTU.COM) and [http://ubuntu.com](http://ubuntu.com) both take you t Ubuntu's home page.

---

### Post by jfinkels on 2007-08-21
> **daveshields said:**
> Google is our friend. A search on "regular expression to parse url" led to the post "RegEx to Match a URL" [http://www.forta.com/blog/index.cfm?mode=entry&entry=A61B9FF5-3048-80A9-EF09C0A7F1E9FBD3](http://www.forta.com/blog/index.cfm?mode=entry&entry=A61B9FF5-3048-80A9-EF09C0A7F1E9FBD3)

I can't assert this is right. But if you search around and find two folks agreeing in the same solution that may give you more confidence.

You need the "-i" to ignore the case. This is right since the case used in a URL doesn't matter. For example, [http://UBUNTU.COM](http://UBUNTU.COM) and [http://ubuntu.com](http://ubuntu.com) both take you t Ubuntu's home page.

And to clarify the other options you may have used, "-o" will match **O**nly the part of the line that matches the regular expression (as opposed to the whole line containing the string that matches the regular expression). "-e" signifies that the next argument will be a regular expression (surrounded by quotes). Read more in the man page for grep:```
man grep
```

---

### Post by kofkof_00 on 2007-08-21
Wow...

I drove home from work feeling pretty bad. I had, after all, spent the day reading howto's, man pages, and tutorials concerning grep.

I had posted a the very end of the day and i was quite surprised to see that I had 4 answers in the time that it took me to drive home!

I am going to try the simpler commands and hopefully this will work.
If it does, it will greatly help in automating a task @ work. :D 

Thank you all for such prompt answers!

---

### Post by jfinkels on 2007-08-21
> **kofkof_00 said:**
> Wow...

I drove home from work feeling pretty bad. I had, after all, spent the day reading howto's, man pages, and tutorials concerning grep.

I had posted a the very end of the day and i was quite surprised to see that I had 4 answers in the time that it took me to drive home!

I am going to try the simpler commands and hopefully this will work.
If it does, it will greatly help in automating a task @ work. :D 

Thank you all for such prompt answers!

You should never be afraid to post in the forums here...two heads are better than one, and infinite heads are better than two.

Let us know how it goes and if you need any more help.

---

### Post by kofkof_00 on 2007-08-22
Well the results are certainly better than what I had prior.

(?:([^:/?#]+):)?(?://([^/?#]*))?([^?#]*)(?:\?([^#]*))?(?:#(.*))? does not work with "bash: syntax error near unexpected token `('" as the output. Sorry Daveshields, that was the same error I got with the expression that regexlib.com said would do the trick.

I think this expression might work in a different environment. (read redhat or some other distro) 

grep -o -P 'http:(.*?)\.exe also doesn't work with the -P perl parameter not being supported.
This one was a suggestion from a co-worker who incedently said that I should just learn perl and that it would be a better solution than trying to grep it...

grep -i "http[s]*://\(www\)*\..*\.com[/]*" index > justurls requires that I convert it to 
grep -i "http[s]*://\(www\)*\..*\.com[/]*" index[COLOR="Red"].txt[/COLOR] > justurls[COLOR="Red"].txt[/COLOR] and add the -o argument. to get a closer result to what I am gunning for.

Stangely, when I substitute .com with .exe the results become much less coherent. The original query gave me pretty much just the urls ending with .com with the occasional glitch where the rest of the line including the tab delimeter and timestamps would be included.

when I do  grep -i -o "http[s]*://\(www\)*\..*\.exe[/]*" index.txt > exelog.txt I get the urls that end in exe AND the timestamps, the tab delimeter and the name of the exe... :confused:

I'm getting there, it's just a little more complicated than I thought it would be.

---

### Post by Cappy on 2007-08-22
Could you please post a sample if you have any more problems?

Based on the problem you have said, I made some improvements though:
```

grep -oi '\(http[s]*://\|www\.\)[^[:SPACE:]]*' index.txt > justurls.txt

```

---

### Post by kofkof_00 on 2007-08-22
Amazing!

That one did it. I now have a list of urls distilled from the index.txt!

All I had to do then is grep -o "http[s]*://\(www\)*\..*\.exe[/]*" justurls.txt > exelog.txt and now I have a list of urls that point ONLY to downloaded exe's!

YES YES YES! This is freakin AWSOME! Thankyou Cappy, jfinkels, this brings me that much closer to finishing my most awsome automation project.

(This also silences the merry band of devs @ work who said that it would be impossible to achieve & I should use perl, python, c++, c sharp, or a divining rod to achieve this!)  :lolflag:

---

### Post by Cappy on 2007-08-22
Just to be clear, you can put this in one line of code like so:
```

grep -oi '\(http[s]*://\|www\.\)[^[:SPACE:]]*' index.txt | grep '\.exe$' > justexes.txt

```
or
```

grep -oi '\(http[s]*://\|www\.\)[^[:SPACE:]]*\.exe' index.txt > justexes.txt

```

---

