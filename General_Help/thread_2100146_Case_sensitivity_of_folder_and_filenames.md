---
title: "Case sensitivity of folder and filenames"
date: 2012-12-31
forum: General Help
---

### Post by Don Barnett on 2012-12-31
I know that this is not really an OS issue but I think one of you might have a good answer.  I have been running on Ubuntu for a long time and have gotten in the apparently bad habit of using upper/lower case folder and file names.  I was in the Bing webmaster area trying to figure out why so few of my pages were being indexed and by accident saw that they were referring to my pages all in lower case and of course when I clicked on the link it came back with page not found.  I have many many folders and pages that are mixed case.

1.  Is this really a problem as Windows doesn't distinguish between upper and lower case? ( I am verily sure Bing and others are running as Windows servers )

2 If it is an issue what would be the best work around short of renaming everything? (there are over 30k pages)

Thanks in advance for any help you can give.

Don

---

### Post by vasa1 on 2012-12-31
Interesting question even though I don't understand quite a bit. Could you please explain what you mean by "trying to figure out why so few of my pages were being indexed"? Do you mean that your pages are under-represented in search results when using Bing as the search engine?

---

### Post by Don Barnett on 2013-01-01
Thanks for the reply.

If I go into Bing Webmaster tools and look at the Reports & Data only 109 pages of over 31,000 unique pages submitted in the sitemap.xml and a "product listing" page are indexed whereas at this time over 22,000 are indexed on Google. The actual page names in the list are in Mixed Upper/lower case and none of the pages listed are indexed on Bing.  I am going to do a experiment and produce a 1000 pages in all lower case and submit the listing file to Bing and see if they get indexed.  I will post back here what happens.  Hopefully it won't screw things up to badly.

Don

---

### Post by eazar001 on 2013-01-01
Why don't you just generate a directory listing, and output all of the listing to awk to capture field 1. From then on pipe it to xargs and rename every instance of a capital letter to the lowercase version (use the ASCII keymap or something).

---

