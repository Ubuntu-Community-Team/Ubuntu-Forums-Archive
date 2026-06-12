---
title: "Script for downloading the latest file from a website?"
date: 2019-05-31
forum: General Help
---

### Post by panja on 2019-05-31
I'm using a Dreamcast emulator (Redream) on my Ubuntu install.
This is a WIP and almost everyday there are new releases with new features or bug fixes.
There for using the latest version is much wanted.

Redream is "installed" in directory: ~/redream/

What I want is a script with the following:
[LIST=1]
[*]Delete the old executable
[*]Download the latest (Linux) version from: [https://redream.io/download/](https://redream.io/download/)
[*]Untar the download file
[*]Delete the downloaded tar file
[*]Profit
[/LIST]

The only step I'm strucling with is step 2.
How can I download the latest version from the website?

Any help is appreciated.

---

### Post by TheFu on 2019-05-31
wget or curl once you know the actual DL URL, but only if they don't insist on putting javascript "ok" buttons as required.  If they do, then look for a website testing tool to emulate the javascript aspects.  Most have to run inside a browser, which will sandbox the other aspects away.

Good news. They don't have a JS button!

The real link seems to be [https://redream.io/download/redream.x86_64-linux-v1.3.1-681-g241b63c.tar.gz](https://redream.io/download/redream.x86_64-linux-v1.3.1-681-g241b63c.tar.gz) for today and there is a 'linux' on the same line.  So, you can "scrape" the screen using any tool you like, look for lines with a URL and Linux to get a short list of download files.  If those lines sort alphabetically in a good way, then you just want the first line or the last line found.  Remove everything before and after the download URL and have wget or curl grab the file. Probably worth checking if you have a local copy already first.

This is a good beginner scripting problem that can be solved in bash, python, perl, ruby, go, ... fairly easily. I think it is about 5 lines of perl, awk or 15 lines in bash.

And if everyone does this, they will change the webpage to make it harder to grab.

If it was me, I'd use the 8 month old "stable" release, but knock yourself out.

For the bash solution, you'll want to use curl, grep, sed, head, tail and either curl or wget.

Ah ... I see they have a redirection to register ... ouch. If your tool doesn't allow cookies, you'll never get to the download page. I think curl can do that, but you'll need to pass in your login credentials.

It might not be worth the effort to do the download part of the script, but you can certainly automate the remaining parts to save 30 seconds and human errors.

[https://www.tldp.org/LDP/abs/html/](https://www.tldp.org/LDP/abs/html/) will be helpful, but if you can find a 20 yr old *Unix Power Tools* book at Goodwill for $1, everything inside there should still be relevant for scripting like this.  
Or just use python/perl/ruby/go ... that you already know.

---

### Post by panja on 2019-06-01
Thanks for all the info.
A bit overwhelming but I'll try to make the best of it.

---

