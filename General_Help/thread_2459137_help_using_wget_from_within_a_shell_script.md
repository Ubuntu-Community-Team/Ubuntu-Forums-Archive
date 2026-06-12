---
title: "help using wget from within a shell script"
date: 2021-03-11
forum: General Help
---

### Post by jcdenton1995 on 2021-03-11
Hello all,

So I'm writing a little shell script which will perform all the actions necessary to update my android phone, which is relatively laborious as it runs an unofficial build of lineageOS, meaning that many operations need to be performed manually every single time it's updated, like restoring contacts, messages, reinstalling apps etc. I've got the core functions of the script sorted, but I still have to manually download the most recent build, as well as all my apps, using a web browser. Ideally I would like to use wget to automatically retrieve the latest versions of the files I need when the script is run, but there are a couple of problems

Because each new lineageOS build is posted to the maintainers google drive as a new file, as opposed to an updated version of the same file, I think I'm right in thinking that wget's '--timestamping' feature won't work (unless I download the entire repo, in which case it would work but it would be a rubbish workaround). This isn't such an issue as the bulk of the manual work is actually downloading all my apps, however the same thing applies. For example [this page]("https://apkpure.com/firefox-browser-fast-private-safe-web-browser/org.mozilla.firefox") is where I download Firefox for android, but I have no idea how I would make wget download the latest version while intelligently choosing the correct CPU architecture for my device. I wondered whether there was some way to implement wget within the script and perhaps use regular expressions to select the correct download link (assuming some sort of consistent naming convention is in use)

Basically I don't understand how wget interacts with the webpage / server and have no idea where to begin. Perhaps I can't do this using BASH / wget and it would require another scripting language? I'd love to hear what some options may be from someone who understands it a little better.

---

### Post by TheFu on 2021-03-11
First, websites that use Javascript to hide the actual download links won't work with wget. You'll need some sort of web-browser simulation/testing tool.  These are usually large and complex.  Portia is one.  There are lots of others.  [https://github.com/scrapinghub/portia](https://github.com/scrapinghub/portia)

If you can get a list of the download URLs from a webpage, then you can use sed regex to remove all the uninteresting parts 
OR
use sed to only pull out the interesting parts.
Which why depends on your sed/regex-fu.  Usually, whenever I need to put stuff into an array, like lines from a webpage, I want a better language than bash.  That's where something like perl, python, ruby come in handy.  Then you can go through each line searching for URLs that have download filenames that match the pattern you seek and remove the stuff before and after that link/URL.

What you are left with is just a small list - say less than 50 URLs with URLs that need a little more filtering.  What filtering is needed completely depends on how each download file gets named.

[https://d-02.winudf.com/b/APK/b3JnLm1vemlsbGEuZmlyZWZveF8yMDE1Nzk0ODgzX2Y0Zjc1NGE4?_fn=RmlyZWZveCBCcm93c2VyIGZhc3QgcHJpdmF0ZSBzYWZlIHdlYiBicm93c2VyX3Y4Ni4xLjFfYXBrcHVyZS5jb20uYXBr&_p=b3JnLm1vemlsbGEuZmlyZWZveA&am=zpBSmcn89elPcB6OBNG9lw&at=1615500572&k=3002635e088dc2d61b1def89d5c23408604be731](https://d-02.winudf.com/b/APK/b3JnLm1vemlsbGEuZmlyZWZveF8yMDE1Nzk0ODgzX2Y0Zjc1NGE4?_fn=RmlyZWZveCBCcm93c2VyIGZhc3QgcHJpdmF0ZSBzYWZlIHdlYiBicm93c2VyX3Y4Ni4xLjFfYXBrcHVyZS5jb20uYXBr&_p=b3JnLm1vemlsbGEuZmlyZWZveA&am=zpBSmcn89elPcB6OBNG9lw&at=1615500572&k=3002635e088dc2d61b1def89d5c23408604be731) is the link I ended up with going through the site. They do that to track and to make the URL unique and to make it live for only a few minutes before it is removed.  Because I don't trust that website, I won't allow javascript from it.

The downloaded filename looks like .... 
Firefox*v86.1.1_apkpure*.apk
So if you can get that list from somewhere, you'll have a pattern to find.  Then just sort and got with the highest number as the one you grab and send to wget, if you can get a direct list, which I don't think is possible. I don't see anything related to the ARM architecture in the filename.

There's a free ebook called _Automate the Boring Stuff_ which gets into stuff like this, but it doesn't address the Javascript URL generation problem either.  Newer versions of the book are sold. [https://github.com/zspatter/automate-the-boring-stuff](https://github.com/zspatter/automate-the-boring-stuff)

---

### Post by jcdenton1995 on 2021-03-11
Thanks, this is really helpful. So what you're saying is that the site actually uses java script to generate a unique link for each downloader on the fly, instead of having a static one that simply points to a resource? Which means it doesn't provide a list of static links that can be retrieved and processed to find the relevant one?

---

