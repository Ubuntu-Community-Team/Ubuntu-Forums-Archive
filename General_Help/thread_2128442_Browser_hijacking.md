---
title: "Browser hijacking"
date: 2013-03-23
forum: General Help
---

### Post by Barney-R on 2013-03-23
HELP!!!

Firefox appears to have been hijacked. Sometimes I can get to sites, but at other times I'm being redirected to

[http://www.purchasereviews.net/donate.php](http://www.purchasereviews.net/donate.php)

... which in turn quickly re-directs, via Google (or something claiming to be Google) and a very brief advert for WalMart, to

[http://adf.ly/noscript.php?t=ck](http://adf.ly/noscript.php?t=ck)

... where yesterday there was a message saying I can't continue unless I enable cookies.

Today though, this has changed to a page "inviting" me to choose a "free gift" (of malware probably).

I first noticed this when I tried to use the BBC site, where **every** link had changed to the "purchasereviews" hijacker.

ClamTK finds nothing. I've tried to get AVG, but the download link there is hijacked too.

I'll be off line for a couple of days, but I'll be VERY grateful if someone can come up with a fix. If not, I'll have to ditch FireFox.

---

### Post by carl4926 on 2013-03-23
what happens if you rename .mozilla to .mozilla-backup?Then start FF

---

### Post by spiderpan on 2013-03-23
I have the same problem

> **carl4926 said:**
> what happens if you rename .mozilla to .mozilla-backup?Then start FF

it seems to work, I used the "new" firefox for a while and the problem did'nt appear again
all we have to do is recover the bookmarks and reinstall the extensions

thank very much

and my apologies for my poor english

---

### Post by Benibur on 2013-03-23
I have exactly the same pb !?!

But i don't want to loose my ff profile !

Any idea of the cause ? any other solution ?

---

### Post by carl4926 on 2013-03-23
> **Benibur said:**
> I have exactly the same pb !?!

But i don't want to loose my ff profile !

Any idea of the cause ? any other solution ?

Save the latest .json file
Start a clean .mozilla and then import the .json

---

### Post by vasa1 on 2013-03-23
> **carl4926 said:**
> Save the latest .json file
Start a clean .mozilla and then import the .json
I don't understand this ^^^. What exactly does it do?

---

### Post by carl4926 on 2013-03-24
The .json file is more complete than say your bookmarks exported as a .html file.json will put your bookmarks back in place, including the bookmarks toolbar and also your cookies and login infoThe .json file can be exported or you can find a bunch of them in .mozilla/firefox/profile/bookmarksbackup

---

### Post by csbened on 2013-03-24
What is the cause of this ? How can be this achived on Ubuntu ? A virus ?

---

### Post by ManamiVixen on 2013-03-24
[**[COLOR=#000000]csbened[/COLOR]**]("http://ubuntuforums.org/member.php?u=512505") No, more like a Firefox compatible malicious script. it essentialy modified Firefox by adding changes in the settings folder of the Users account. You don't have to worry if you have a Adblocker installed for Firefox.

---

### Post by sandyd on 2013-03-24
Ghostry probably helps too :D

---

### Post by Barney-R on 2013-03-25
I've renamed the .mozilla folder as suggested, and so far it seems to have worked.

THANK YOU.

Presumably it is now safe to delete the renamed folder, but I'll wait a while before doing that.

The only thing I did differently that day was to let a friend show me one of his favourite sites. Presumably that was where I acquired the infection. The site was called something like "Mami's s**t", which doesn't sound very wholesome anyway.

I certainly won't be going there again.

I won't mark this thread as "Solved" for a few days until I'm certain the hijacker is gone, and I'll be following the discussion in the hope of learning more about this particular item of malware.

---

### Post by SeijiSensei on 2013-03-25
Oh, come on now.  Mami is just a cute fourteen-year-old [girl]("http://th00.deviantart.net/fs70/PRE/i/2011/289/6/f/mami_tomoe_vector_by_hombre0-d4d2anx.png") who likes to drink tea, eat cake, and kill witches.  How much more wholesome can you get?

---

### Post by Barney-R on 2013-03-25
Perhaps it's a different Mami. I don't know. I just saw page after page of videos. I don't even know what they were about. There wasn't much time, so I bookmarked the site and said I'd check it out later.

I should be able to provide more information later this week, when I've had a chance to find out from him what the URL is.

From a StartPage search, it seems likely that it could have been grizzom.blogspot.com, but I need to check, and I'm not going back to that place until I'm certain it's clean.

I'm not even saying it WAS the "Mami's s**t" site that installed the hijacker, just that it seems the most likely suspect as I normally only visit a few trusted sites. A trusted friend comes over for a visit, shows me this one site, and that evening I've got an infection.

---

### Post by SeijiSensei on 2013-03-25
I was making a joke.  Mami is a relatively common Japanese girl's name, and there are many others who might have been on the site you mentioned besides young Ms. Tomoe of *Madoka Magica* fame.  A quick search for "mami gravure idol" brings up lots of alternatives, many of them including videos. You can see Tomoe Mami in action at [Crunchyroll](http://www.crunchyroll.com/puella-magi-madoka-magica).  She first appears near the end of episode one complete with her impressive battle theme.

As others have remarked, AdBlockPlus and Ghostery can help protect you against this type of junk.

---

### Post by Barney-R on 2013-03-25
No problem SeijiSensei. We all need a bit of light relief from time to time.

I already had AdBlock Plus and Ghostery installed prior to the infection, and now I've installed BrowserProtect, so I can hope it won't happen again (everything crossed).

I've been finding a lot on line about something called (if I've got this right) "Google redirect virus" (a browser hijacker, not a virus) that seems to fit. It's described as something pretty nasty and difficult to get rid of, but most of the posts I've found seem to be two or three years old.

I haven't had any problems since renaming the .Mozilla folder, so I can hope that's the answer. I'll give it a couple of days to be sure, then delete the folder, after which I'll mark this thread as solved - - unless the hijacker comes back that is.

---

### Post by PJW9779 on 2013-03-26
Based on the json suggestion I did a search on root for all json's and focussed on the last additions.
One sprang out : bokehpassion_02.persona.json.

Never heard of it, don't use it, seems some gimmick.
But after deleting it and restarting FF, the hijack seems to be gone.
And it is FF related, no issues with Konquerer.

---

### Post by carl4926 on 2013-03-26
the .json files are in the .mozilla profile folder

For me that is:  ~/.mozilla/firefox/3vbwf2j7.default/bookmarkbackups/

---

### Post by slickymaster on 2013-03-26
> **vasa1 said:**
> I don't understand this ^^^. What exactly does it do?

Since version 3.0, Firefox regularly creates a file for for bookmark backup in JSON format in "bookmarkbackups" folder in your profile. Firefox version 1.0 - 2.0 stored bookmark backup in HTML.
When importing a *.json file to a new profile, it will replace any existing bookmarks with those in the *.json file.

---

### Post by Buntu Bunny on 2013-03-26
I appreciate the head's up, having recently returned to FF from Opera. I do use Adblock Plus also HTTPS Everywhere. Hopefully there will be no problems.

---

### Post by Barney-R on 2013-03-27
I haven't had any more problems, thank goodness, so I've deleted the old (renamed) .mozilla file and am rebuiding my bookmarks manually. They needed "thinning out", so for me, this is the best way.

I'll mark the thread as solved (and hope it is).

Thanks again for all your help.

---

### Post by Barney-R on 2013-03-27
Now I've got another problem. I click on "Thread Tools" and there's no option to mark the thread as solved.

I realise a few changes have been made to the forum recently, so can someone point me in the right direction? Thanks.

---

### Post by Laobi on 2013-03-27
Here is the temporary solution on how to mark the thread solved:
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by subsven on 2013-03-27
> **Barney-R said:**
> HELP!!!
 Firefox appears to have been hijacked. Sometimes I can get to sites, but at other times I'm being redirected to
[http://www.purchasereviews.net/donate.php](http://www.purchasereviews.net/donate.php)


I had the same problem. It seemed to be caused by a Firefox Extension called "Youtube Mp3 Downloader 2.1".

If you look at the source code on [https://addons.mozilla.org/en-US/firefox/files/browse/198137/file/chrome/content/overlay.js#top](https://addons.mozilla.org/en-US/firefox/files/browse/198137/file/chrome/content/overlay.js#top) you'll find many lines like these:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]for (var i=0; i<allLinks.length; i++) {
  allLinks[i].href="http://www.purchasereviews.net/donate.php";
}[/TD]
[/TR]
[/TABLE]


So it seems pretty obvious that this at least this extension caused the redirects ...

Sven

---

### Post by spiderpan on 2013-03-28
> **subsven said:**
> 
If you look at the source code on [https://addons.mozilla.org/en-US/firefox/files/browse/198137/file/chrome/content/overlay.js#top](https://addons.mozilla.org/en-US/firefox/files/browse/198137/file/chrome/content/overlay.js#top) you'll find many lines like these:
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]for (var i=0; i<allLinks.length; i++) {
  allLinks[i].href="http://www.purchasereviews.net/donate.php";
}[/TD]
[/TR]
[/TABLE]
So it seems pretty obvious that this at least this extension caused the redirects ...
Sven

That seems to be the right one
The problem reappeared few days after I had deleted the old mozilla folder, so I unistalled the extension and everithing works fine now
thanks \\:D/

---

### Post by Barney-R on 2013-03-29
Thanks for that, subsven. Source code doesn't mean very much to me since the old Commodore 64 assembly language, but that last line is pretty obvious, even to me.

Downloading from YouTube can be a bit of a minefield where copyright issues are concerned, but I do occasionally use one or other of the download applications where the copyright owner makes it clear that he/she **wants** people to download the video or it's audio.

Youtube Mp3 Downloader 2.1 is clearly MALWARE, so AVOID IT.

At least it was "self-contained" within FireFox rather than infecting Ubuntu, so all I had to do was delete the .mozilla folder, and I didn't even lose my e-mails or settings in Thunderbird.

---

