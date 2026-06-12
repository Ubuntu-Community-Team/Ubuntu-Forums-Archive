---
title: "command line file editing"
date: 2014-05-04
forum: General Help
---

### Post by jtpratt on 2014-05-04
I have a list of 1,600 URL's like this:
[http://www.website.com/2014/04/03/some-page-name.aspx](http://www.website.com/2014/04/03/some-page-name.aspx)

I want to make a list of 301 redirects with a structure that doesn't have dates or file extensions

I need the file to be like this
Redirect 301 [http://www.website.com/2014/04/03/some-page-name.aspx](http://www.website.com/2014/04/03/some-page-name.aspx) [http://www.website.com/some-page-name](http://www.website.com/some-page-name)

I can make a script to remove any bit of that, and even add the Redirect 301, but I can't seem to make the script take a line like this:
[http://www.website.com/2014/04/03/some-page-name.aspx](http://www.website.com/2014/04/03/some-page-name.aspx)

and make it this:
[http://www.website.com/2014/04/03/some-page-name.aspx](http://www.website.com/2014/04/03/some-page-name.aspx) [http://www.website.com/2014/04/03/some-page-name.aspx](http://www.website.com/2014/04/03/some-page-name.aspx)

any sed, awk, or other scriptaculous things I can do?

---

### Post by erind on 2014-05-04
> **jtpratt said:**
> I have a list of 1,600 URL's like this:
[http://www.website.com/2014/04/03/some-page-name.aspx](http://www.website.com/2014/04/03/some-page-name.aspx)

I want to make a list of 301 redirects with a structure that doesn't have dates or file extensions

I need the file to be like this
Redirect 301 [http://www.website.com/2014/04/03/some-page-name.aspx](http://www.website.com/2014/04/03/some-page-name.aspx) [http://www.website.com/some-page-name](http://www.website.com/some-page-name)

[...]

One way with awk:

```
awk '{ rec=$0; gsub(/[0-9]+\/[0-9]+\/[0-9]+\/|\.[^.]+$/,"") ; print "Redirect 301 " rec " " $0 }'  filename

```
The code is based on your posted input, however the regex part inside gsub can be made stricter if needed.

---

### Post by jtpratt on 2014-05-05
> **erind said:**
> One way with awk:

```
awk '{ rec=$0; gsub(/[0-9]+\/[0-9]+\/[0-9]+\/|\.[^.]+$/,"") ; print "Redirect 301 " rec " " $0 }'  filename

```
The code is based on your posted input, however the regex part inside gsub can be made stricter if needed.

that was great, thanks!  It only printed to the screen, so I updated like this to print to a new file:

awk '{ rec=$0; gsub(/[0-9]+\/[0-9]+\/[0-9]+\/|\.[^.]+$/,"") ; print "Redirect 301 " rec " " $0 }'  urls2.txt > urls3.txt && mv urls3.txt urlsfinal.txt

---

### Post by jtpratt on 2014-05-05
I guess what I thought would work at first needs some modification.  for instanced, let's say I have a line like this:
[www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page)

I'm building a file a 301 redirects (1,600 of them).
so if I use that code I'll get
Redirect [www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page) [www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page)

so let's say I find and replace the dates out - I'll remove them from both entries.

What I need in the end is for each line to have dates in the first entry, and no dates in the second like this:
Redirect [www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page) [www.website.com/this-is-my-page](www.website.com/this-is-my-page)

the URL's all have varying length.

1.  is there a way I can remove the date sub-dirs from only the second URL?

2.  if not I can build 2 files, one with dates and one not.  Is there a way to merge the 2 files together where the right lines line up?

---

### Post by steeldriver on 2014-05-05
You could use awk to split the URL into /-delimited fields, then print out the ones you want to keep e.g. if

```

url='www.website.com/2014/4/30/this-is-my-page'

```
then
```

$ awk -F/ '{print "Redirect",$0,$1"/"$NF}' <<< "$url"
Redirect www.website.com/2014/4/30/this-is-my-page www.website.com/this-is-my-page

```

or something like this with sed, which just deletes anything matching (more-or-less) /yyyy/mm/dd?

```

$ echo "Redirect $url" $(sed -r 's|/[0-9]+/[0-9]+/[0-9]+||' <<< "$url")
Redirect www.website.com/2014/4/30/this-is-my-page www.website.com/this-is-my-page

```

---

### Post by jtpratt on 2014-05-06
well, here's the thing.  I can remove dates from a line no problem.  The rewrite rules are basically redirect this URL to that URL
My original URL is this:
[www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page)

The rewrite rules need to be redirect this URL to the new URL like this:
Redirect 301 [www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page) [www.website.com/this-is-my-page](www.website.com/this-is-my-page)

Notice the URL appears twice in that line - that's the end product of what I need.

If you look through the posts here since the beginning I got some code to repeat the same URL on a line.
so I can turn this:
[www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page)

inito this:
[www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page) [www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page)

and I can prepend all the lines with Redirect 301 like this:
Redirect 301 [www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page) [www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page)

what I cannot do is - the date sub-dirs appear twice (/2014/4/30).  I want the date to appear in the first URL (the original location of the page), but be removed in the second URL (the new location of the URL)
so if I have this:
Redirect 301 [www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page) [www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page)

how do I remove the dates from only the second URL in 1,600 lines?  The URL will vary - so it's not like I can character count.  As I mentioned, maybe an option is to make 2 files of URL's - one with dates, and one without - and merge them together?  I just need a way to merge each exact line - separated by a space.

Again - thx for everyone's help, my regex and find / replace skills are really lacking (even though I've been on Ubuntu for 8-9 years).

---

### Post by steeldriver on 2014-05-06
isn't that exactly what I posted above? :confused:

or are you asking about how to read the URL lines from the file?

---

### Post by jtpratt on 2014-05-06
I'm not sure - sorry I'm a webdev with some hacking skills going back to Perl and some shell, but I don't totally get what you posted.  In the first one you assign a URL to something.  In the second you prepend the line - I get that, but then the second line has this:
Redirect [www.website.com/2014/4/30/this-is-my-page](www.website.com/2014/4/30/this-is-my-page) [www.website.com/this-is-my-page](www.website.com/this-is-my-page)

so I don't get that...I don't get what the $0, $1, and $NF vars come from.

the last one:
$ echo "Redirect $url" $(sed -r 's|/[0-9]+/[0-9]+/[0-9]+||' <<< "$url")

you said it removes /yy/mm/dd/ - but wouldn't that remove it from both URL's?  How I limit it to just the last one?

I guess the main thing is - I didn't understand if your approach was to remove the dates from a file with 2 URL's per line, or 2 files with single rows of URL's that get merged together.

Sorry to be such a PITA rear here, my knowledge in this area stopped at command line find and grep operations a decade back.

---

### Post by steeldriver on 2014-05-06
in

```
echo "Redirect [COLOR=#008000]**$url**[/COLOR]" [COLOR=#0000ff]**$(sed -r 's|/[0-9]+/[0-9]+/[0-9]+||' <<< "$url")**[/COLOR]
```

the [COLOR=#008000]**$url**[/COLOR] part is the original, unmodified URL string and the [COLOR=#0000ff]**$(sed -r 's|/[0-9]+/[0-9]+/[0-9]+||' <<< "$url")**[/COLOR] part is the same string after stripping the date

---

### Post by Lars Noodén on 2014-05-06
> **jtpratt said:**
> 
so I don't get that...I don't get what the $0, $1, and $NF vars come from.


They are built into [awk](http://www.grymoire.com/Unix/Awk.html).  $0 stands for the whole input record.  A record is usually a single line.  $1 stands for the first field, as defined by the pattern in the Field Separator, FS.  $2 would be the second field, $3 the third field and so on.  NF is a built-in variable, one of several, but it contains the number of fields found in the current record (line).   

You mentioned perl, if that is easier to work with for you, something like this might work:

```

perl  -w -p -e 's|^(.*//[^/]+/)(\d{4}/\d{2}/\d{2}/)(.*)$|Redirect 301 $1$2$3 $1$3|' < yourfile

```

I'm not sure that's clearer to read though.

---

### Post by steeldriver on 2014-05-06
Oops so I guess I misunderstood, you want to EDIT the file in place - I was assuming you wanted to read the lines and CREATE the redirect strings from them on the fly

```

$ sed -r 's|^([^/]+)(/[0-9]+/[0-9]+/[0-9]+)(.*)$|Redirect & \1\3|' urls.txt
Redirect www.website.com/2014/4/30/this-is-my-page www.website.com/this-is-my-page

```

where
```

$ cat urls.txt
www.website.com/2014/4/30/this-is-my-page

```

Adding -i should make it interactive - but Lars Noodén's perl expression is better I think (allows for http:// prefix if present)

---

### Post by jtpratt on 2014-05-06
thanks to both of you! 

so with this one:
echo "Redirect $url" $(sed -r 's|/[0-9]+/[0-9]+/[0-9]+||' <<< "$url")

it looks like it will do everything I want, but how do I get it to read each line as $url?  At least now based Lars comment - I understand that with awk $0 is the full line.  With sed it's not clear how to tell it which file to use, or how $url become each line entry?

Again - thank you for your patience and continued help.

---

### Post by Lars Noodén on 2014-05-06
You could try wrapping it in a loop.

```

for url in $(cat ./yourfile);do echo $url;done

for url in $(cat ./yourfile);do echo "Redirect $url" $(sed -r 's|/[0-9]+/[0-9]+/[0-9]+||' <<< "$url");done

```

sed (Stream EDitor) takes only a stream of characters, it's up to other pieces to break them into lines.

---

### Post by jtpratt on 2014-05-06
thanks to everyone!!  I finally got this all sorted out.

---

