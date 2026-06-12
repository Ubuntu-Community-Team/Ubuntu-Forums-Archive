---
title: "Firefox double toolbar help/ file edit"
date: 2008-05-30
forum: General Help
---

### Post by jaysons on 2008-05-30
I'm trying to do a simple task of copy paste to a file and rename. But it's not working. 
I'm trying to add: /* Multi-row bookmarks toolbar */
#bookmarks-ptf {display:block}
#bookmarks-ptf toolbarseparator {display:inline} 

to the bottom of the userChrome-example.css file and re-name userChrome.css

end result is a double bookmarks toolbar in firefox.

how I am doing it is: sudo nautilus then I browse to usr/lib/firefox-3.0b5/defaults/profile/chrome 
this is where I find the userChrome-example.css file. 

In other fourms I ask how to do it and people do just what I am saying and it works for them...the only thing I can think of is I am editing the file with "text editor" which should work. Also the userChrome-example.css file should be in the /firefox folder but it's not, I found it in the /firefox-3.0b5 folder....Help?

---

### Post by y-lee on 2008-05-30
It appears to me you are editing and then saving that file as superuser, that would then give it root permissions. That seems wrong to me and may be the source of your problems.

---

### Post by jaysons on 2008-05-30
I cannot save the file as user, it says I don't have permission, so I logg in as root then I can save...

---

### Post by y-lee on 2008-05-30
You need to open the file userChrome-example.css as normal user and then save it to your own firefox profile. This is in a hidden directory in your home folder

```
/home/username/.mozilla/firefox/xxx.default/chrome
```

where *username* is your own *username* and *xxx* is a seemingly random string of characters.

Also in this directory one should also find another copy of userChrome-example.css.

---

### Post by jaysons on 2008-05-30
/home/username/.mozilla/firefox/xxx.default/ no chrome folder or file 
should I create a chrome folder and copy the userChrome-examples.css file to it and then edit it as userChrome.css 
???

---

### Post by y-lee on 2008-05-30
That is what i would try. Note I am using firefox 2.0.x and not firefox 3 but it should be similar

---

### Post by jaysons on 2008-05-30
still no luck...everything looks as it should but I still have a single bookmark toolbar...
/home/user/.mozilla/firefox/xxx.default/chrome

all files there, (3) userChrom.css userChrome-example.css userContent-examples.css

saved userChrome.css as user not root..

files are also in usr/lib/firefox-3.0b5/defaults/profile/chrome
which is where I found the original userChrome-example.css and userContent-examples.css

---

### Post by y-lee on 2008-05-30
hmmm, not sure :confused: What are the permissions on that file ?

---

### Post by jaysons on 2008-05-30
original userChrome-examples.css is root read only

here is link to another forum where people were doing it and trying to help me --scroll down a little tittle is "Equivalent to?"   

--my screen name on this forum is Stimp--

[http://columbus.craigslist.org/forums/?forumID=1991](http://columbus.craigslist.org/forums/?forumID=1991)

---

### Post by y-lee on 2008-05-30
Change your code to


```

/* Multi-row bookmarks toolbar */
#bookmarks-ptf {
display:block !important;
}
#PersonalToolbar:not([collapsed]) #bookmarks-ptf > toolbarbutton {
visibility: visible !important;
}
#bookmarks-stack {
overflow: visible !important;
}
#bookmarks-stack > .bookmarks-toolbar-overflow-items {
display: none !important;
}
```

---

### Post by jaysons on 2008-05-30
I replaced

```
/* Multi-row bookmarks toolbar */
#bookmarks-ptf {display:block}
#bookmarks-ptf toolbarseparator {display:inline}

```

with

```
/* Multi-row bookmarks toolbar */
#bookmarks-ptf {
display:block !important;
}
#PersonalToolbar:not([collapsed]) #bookmarks-ptf > toolbarbutton {
visibility: visible !important;
}
#bookmarks-stack {
overflow: visible !important;
}
#bookmarks-stack > .bookmarks-toolbar-overflow-items {
display: none !important;
}
```

in both files still no luck..
when I say both files I mean in 
usr/lib/firefox-3.0b5/defaults/profile/chrome
and
/home/user/.mozilla/firefox/xxx.default/chrome

---

### Post by fanderal on 2008-05-31
Saw your post on CL and noticed the format. Dunno if it'll make a difference but this the format of the "userChrome-example.css" file in Debian:

> 
/*
 * Edit this file and copy it as userChrome.css into your
 * profile-directory/chrome/
 */

/*
 * This file can be used to customize the look of Mozilla's user interface
 * You should consider using !important on rules which you want to
 * override default settings.
 */

/*
 * Do not remove the @namespace line -- it's required for correct functioning
 */
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */


/*
 * Some possible accessibility enhancements:
 */
/*
 * Make all the default font sizes 20 pt:
 *
 * * {
 *   font-size: 20pt !important
 * }
 */
/*


---

