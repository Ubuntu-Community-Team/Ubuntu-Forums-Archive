---
title: "How can I find broken links in my website?"
date: 2021-10-22
forum: General Help
---

### Post by Paddy Landau on 2021-10-22
**EDIT**: After searching for two days, I finally found [this online tool]("https://www.deadlinkchecker.com/website-dead-link-checker.asp")! Clearly, my searching skills need improvement.

I am trying to find broken links on my website (hosted with a professional host, *not* with Ubuntu Server).

I've been scouring the 'net for methods. I found many suggestions to use LinkChecker (which no longer works, apparently), several suggestions for online services that no longer exist, and command line suggestions.

For example, I found [How To Find Broken Links &#8230; Using Wget]("https://www.digitalocean.com/community/tutorials/how-to-find-broken-links-on-your-website-using-wget-on-debian-7"), but trying this simply doesn't find the broken link that I already know exists, never mind the ones that I don't know about. I can't figure out where I'm going wrong.

What can you suggest for me to "spider" my website to find broken links?

Thank you

---

### Post by dragonfly41 on 2021-10-22
A couple of links ..
> [COLOR=#000000]Clearly, my searching skills need improvement.[/COLOR]
[https://ahrefs.com/blog/google-advanced-search-operators/](https://ahrefs.com/blog/google-advanced-search-operators/)

and .. use Python instead of tools ..
[https://brianli.com/2021/06/how-to-find-broken-links-with-python/](https://brianli.com/2021/06/how-to-find-broken-links-with-python/)

---

### Post by Paddy Landau on 2021-10-22
> **dragonfly41 said:**
> A couple of links ..

[https://ahrefs.com/blog/google-advanced-search-operators/](https://ahrefs.com/blog/google-advanced-search-operators/)

and .. use Python instead of tools ..
[https://brianli.com/2021/06/how-to-find-broken-links-with-python/](https://brianli.com/2021/06/how-to-find-broken-links-with-python/)
Excellent, thank you!

I don't know Python at all, so I saved the Python version into a file with the header "#!/usr/bin/env python3". I also figured out that I had to install python3-bs4.

When I run it, it finishes almost instantly and gives no output whatsoever.

Do you know what I have to do to make it work?

---

### Post by dragonfly41 on 2021-10-22
try setting root_domain to a known broken link such as

    root_domain = [github.com/mrdoob/three.js/issues/1218]("https://github.com/mrdoob/three.js/issues/1218")

And optionally you could set your script to be executable to run.

P.S. corrected to only show domain .. 

The broken links are gathered into an array .. broken_links = [] .. and you might need extra code to scan the array and print.
There is no print command added I see.

P.P.S.

There is also this ..

[https://validator.w3.org/checklink](https://validator.w3.org/checklink)

---

### Post by TheFu on 2021-10-22
wget won't uncover javascript-generated links.  For that, you'll need a "javascript driver" to click everywhere there's a hot-point on the webpage and I'd probably use a proxy server with the browser that logs all external requests.  Filtering those shouldn't be too hard from the proxy logs.

For simple <a href=" links ... if you have access to the HTML files, just use **fgrep -E** to pull the links.
Depending on the content management tool, there might be a "sitemap" feature which would generate an rss/atom feed with all the links.  

Once all the links are in a file and cleaned up, that can be fed into curl (or something like curl) to see that a HTTP status of 200 is returned. Those are "good links" and any other return needs to be researched more.  The 3xx are redirections.

---

### Post by Paddy Landau on 2021-10-22
> **dragonfly41 said:**
> The broken links are gathered into an array .. broken_links = [] .. and you might need extra code to scan the array and print.
…
[https://validator.w3.org/checklink](https://validator.w3.org/checklink)
Thanks for the suggestions. I don't know Python at all, so I'll forget about the Python alternative.

I tested the W3C validator, and it works well. That's a good one!
> **TheFu said:**
> wget won't uncover javascript-generated links.
That's OK, I don't have any of those.
> **TheFu said:**
> For simple <a href=" links ... if you have access to the HTML files, just use **fgrep -E** to pull the links.
It's a CMS system, so I'd have to spider the website.
> **TheFu said:**
> Depending on the content management tool, there might be a "sitemap" feature which would generate an rss/atom feed with all the links.
Good idea! I should be able to create a sitemap. Thank you

---

### Post by Dennis N on 2021-10-22
I have an internal genealogy website and I recall using a utility that checked the validity of hyperlinks to a specified level and report broken links. I'm sure I did not use an external site. I don't remember the application name, or on which computer it was on, but I will check if I can identify it.

---

### Post by Dennis N on 2021-10-22
The program is called **linkchecker**.

```
dmn@Tyana-vm:~$ apt search linkchecker
Sorting... Done
Full Text Search... Done
daps/hirsute,hirsute 3.0.0-4 all
  DocBook Authoring and Publishing Suite (DAPS)

linkchecker/hirsute 10.0.1-1 amd64
  check websites and HTML documents for broken links

linkchecker-web/hirsute,hirsute 10.0.1-1 all
  check websites and HTML documents for broken links (web client)

w3c-linkchecker/hirsute,hirsute 4.81-10 all
  tool to verify the links in a web page are still valid


```

---

### Post by Paddy Landau on 2021-10-23
> **Dennis N said:**
> The program is called **linkchecker**.
Thanks. I saw this mentioned in several places. You need to add a PPA, but from what I've read, it's no longer supported.

---

### Post by Dennis N on 2021-10-23
> **Paddy Landau said:**
> Thanks. I saw this mentioned in several places. You need to add a PPA, but from what I've read, it's no longer supported.

Oh...my output is from 21.04 repositories (universe). **linkchecker** must be a recent inclusion. Also available in 21.10.
I see it's not in 20.04 repositories.

Note: My installation of linkchecker is on Fedora where I installed it last year. I have noticed over time that Fedora seems to make more packages available in their repositories.

---

### Post by dragonfly41 on 2021-10-23
In Ubuntu 20.04 I found w3c-linkchecker through Synaptic and then various sites ..

[https://metacpan.org/dist/W3C-LinkChecker/view/bin/checklink.pod](https://metacpan.org/dist/W3C-LinkChecker/view/bin/checklink.pod)
It seems that the command to use is .. checklink .. once w3c-linkchecker is installed.

[FONT=monospace][COLOR=#000000]$ checklink[/COLOR]
W3C Link Checker version 4.81 (c) 1999-2011 W3C
[/FONT]

---

