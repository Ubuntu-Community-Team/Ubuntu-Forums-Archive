---
title: "Firefox doesn't show &lt;tr&gt; background-color style on mouseover"
date: 2006-12-12
forum: General Help
---

### Post by miggl on 2006-12-12
Hi all:

I have this weird firefox bug that only seems to happen in Linux (works fine under windows):
The following code will not highlight my row:```
<html>
<head>
<style>
.hover_row
{
	background-color: #ccccff !important;
}
<style>
<head>
<body>
<table>
<tr onmouseover="this.className='hover_row';" onmouseout="this.className='';" style="cursor: pointer;">
<td class="normal_row">test</td>
</tr>
</table>
</body>
</html>
```

However, I have found that if I remove the class from the table cell, the row does highlight. This tells me that the cell style is being rendered on top of, or even replacing the rendering of the row style.

Is there a work-around to this?

Thanks guys and gals!

---

### Post by po0f on 2006-12-12
miggl,

Does something like this work for you?
```
[FONT="Courier New"]<style>
tr:hover {
    background-color: #high-light color;
}
</style>

...

<tr><!-- blah --></tr>

...[/FONT]
```

---

### Post by miggl on 2006-12-12
That produces the exact same results as in my example above, unfortunately. :(

---

### Post by DJ_Peng on 2006-12-12
Can you point to an example of this online? As a Firefox tester I'd like to take a look at it to see if we can file a bug with Mozilla on this.

---

### Post by miggl on 2006-12-12
Sure, you can check it out here: [http://www.emmgee.com/sandbox/firefox_bug/](http://www.emmgee.com/sandbox/firefox_bug/)

---

### Post by DJ_Peng on 2006-12-13
It works fine in the Release Candidate for Firefox 2.0.0.1. It may simply be broken in Ubuntu's builds, which is just one more reason why I rely on Mozilla's builds rather than Ubuntu's.

---

### Post by miggl on 2006-12-13
> **DJ_Peng said:**
> It works fine in the Release Candidate for Firefox 2.0.0.1. It may simply be broken in Ubuntu's builds, which is just one more reason why I rely on Mozilla's builds rather than Ubuntu's.

Good point. Unfortunately Ubuntu won't let me uninstall it using synaptic without removing the entire desktop suite.

How would you recommend to install Mozilla's build? Thanks!

---

### Post by DJ_Peng on 2006-12-13
Yeah, I ran into that as well. I just added the version from Mozilla, then edited the menu to point to what I had just added rather than the "official" version. Also, you can use the "-profilemanager" flag to get into the [Profile Manager](http://kb.mozillazine.org/Profile_Manager) and use your current profile rather than losing all your bookmarks, settings, etc.

---

### Post by miggl on 2006-12-13
Thanks for the tip. I did the same thing, but it doesn't yield any better results than the default Ubuntu Firefox. I JUST downloaded the official release version. Here's the info from the about window:
> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1) Gecko/20061010 Firefox/2.0
Perhaps this has been addressed in a newer build?

---

### Post by miggl on 2006-12-13
I'll answer myself on that one: I just installed the Granparadiso build 3.0alpha1 and it still will not highligh both rows as it should. I have removed all add-ons and extensions. This leads me to believe that this is something either in Ubuntu or in the firefox profile that is causing this.

This is the version info of the build I tested:> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9a1) Gecko/20061204 GranParadiso/3.0a1

---

### Post by miggl on 2006-12-13
Unfortunately it doesn't seem to be associated with the Firefox profile either (I removed the entire .mozilla directory).

Next test will see if it is associated with my Ubuntu profile.

---

### Post by miggl on 2006-12-13
No dice here either. I'm at the end of my rope on this one. Could it be the firefox gnome integration that causes this?

---

### Post by miggl on 2006-12-13
This time I uninstalled all firefox-related entries from synaptic that would let me without having to remove ubuntu-desktop. The problem still persists.

---

### Post by DJ_Peng on 2006-12-13
Ah, ok. GP is in a very early alpha stage and they admit many thing sare broken in it. I had to switch to my Windows boot to get ready for my radio show in the am, but I can confirm that the code works in Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.1) Gecko/20061212 BonEcho/2.0.0.1 for both Linux and Windows. That's in the latest nightly build, although I couldn't find a due date for the expected public release of 2.0.1.

---

### Post by miggl on 2006-12-13
I installed 2.0.0.1 as well, to no avail. :( Here's the version info:> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061208 Firefox/2.0.0.1

I don't think its firefox itself anymore, as you don't have the issue on your machine. I'll try it on another machine where I have a clean install.

---

### Post by miggl on 2006-12-13
Unfortunately that wasn't it either.

I'm running Ubuntu 6.10 with all the updates (and then some) on my regular machine, and Ubuntu 6.10 with a pure CD install and no updates and no frills on my second machine.

Both show the same behaviour when browsing the test page in Firefox.

---

### Post by DJ_Peng on 2006-12-13
But are you using Firefox 2 from the repository or from Mozilla itself? If it's the Ubuntu version you may want to try downloading it straight from Mozilla and seeing if the problem persists. If it does you may want to post something in the [MozillaZine Firefox Support forums]("http://forums.mozillazine.org/viewforum.php?f=38") and see if someone there has any ideas what could be causing the problem.

---

### Post by miggl on 2006-12-13
> **DJ_Peng said:**
> But are you using Firefox 2 from the repository or from Mozilla itself? If it's the Ubuntu version you may want to try downloading it straight from Mozilla and seeing if the problem persists. If it does you may want to post something in the [MozillaZine Firefox Support forums]("http://forums.mozillazine.org/viewforum.php?f=38") and see if someone there has any ideas what could be causing the problem.

Yes, like I said earlier, I downloaded directly from Mozilla.

Now here's the kicker: it doesn't work in Windows Firefox or IE 6 either. (Testing it at work today).

Please try this for me. Copy/paste the following code into and html file on your system. Check if BOTH rows highlight.```
<html>
<head>
<style type="text/css">
.hover_row
{
	background-color: #ccccff;
}

.normal_row
{
	background-color: #ffffff;
}
</style>
</head>
<body>
<table>
<tr onmouseover="this.className='hover_row';" onmouseout="this.className='';" style="cursor: pointer;">
<td class="normal_row">this will not highlight on mouse-over, but it should!</td>
</tr>
<tr onmouseover="this.className='hover_row';" onmouseout="this.className='';" style="cursor: pointer;">
<td>this will highlight on mouse-over</td>
</tr>
</table>
</body>
</html>

```

---

### Post by miggl on 2006-12-13
OK, now this is embarrassing!

Of course TR will render behind TD, because it's its parent. Not sure why I even thought that changing the background color on the TR would overwrite the background color on the TD, which it of course won't!!

Thanks for trying to help, guys! I appreciate that. I apologize for taking up your time with this brain fart. ](*,) :-? :(

---

### Post by DJ_Peng on 2006-12-13
Been there, done that, got way too many tees. I'm glad you were able to get it sorted out.

---

