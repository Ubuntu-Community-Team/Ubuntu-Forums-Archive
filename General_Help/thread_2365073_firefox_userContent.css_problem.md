---
title: "firefox userContent.css problem"
date: 2017-07-02
forum: General Help
---

### Post by ardouronerous on 2017-07-02
Here's the userContent.css:

```
/*
* Use this css file to eliminate problems in Firefox
* when using dark themes that create dark on dark
* input boxes, selection menus and buttons. Put this
* in the ../firefox/default/chrome folder or your
* individual user firefox profile chrome folder.
Special Thanks to http://forums.fedoraforum.org/showthread.php?t=299664 For this code, User: PabloTwo.
Re-Distrobuted By RAVEfinity.
*/
input {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}
textarea {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}
select {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}
input[type="radio"],
input[type="checkbox"] {
border: 2px inset white ! important;
background-color: white ! important;
color: ThreeDFace ! important;
-moz-appearance: none !important;
}
*|*::-moz-radio {
background-color: white;
-moz-appearance: none !important;
}
button,
input[type="reset"],
input[type="button"],
input[type="submit"] {
border: 2px outset white;
background-color: #eeeeee;
color: black;
-moz-appearance: none !important;
}
body {
background-color: white;
color: black;
display: block;
margin: 8px;
-moz-appearance: none !important;
}

```

In previous versions of Firefox, this userContent.css had no problems, but after updating to Firefox 54.0, this is the problem:
[ATTACH=CONFIG]275833[/ATTACH]

As you can see, the checkboxs are barely visible. What should I edit in the userContent.css?

---

### Post by &amp;KyT$0P# on 2017-07-02
I see the same.  It's possible to make the checkboxes a reasonable size, but the "checked" state doesn't show - they all look un-checked.

Maybe worth [filing a bug]("https://bugzilla.mozilla.org/").

---

### Post by vasa1 on 2017-07-02
Try deleting every```
-moz-appearance: none !important;
```Save the file. Restart Firefox. Does that help?

---

### Post by #&amp;thj^% on 2017-07-02
> **vasa1 said:**
> Try deleting every```
-moz-appearance: none !important;
```Save the file. Restart Firefox. Does that help?

+1
And well, ideally, !important should be avoided as much as possible! :) 

Alternatively you can do it with classes (so all your CSS is in the CSS files themselves, and not being directly altered by javascript): [http://jsfiddle.net/FF3mc/4/](http://jsfiddle.net/FF3mc/4/)

---

### Post by ardouronerous on 2017-07-02
> **vasa1 said:**
> Try deleting every```
-moz-appearance: none !important;
```Save the file. Restart Firefox. Does that help?

Yes, it does fix the checkbox issue, but it also caused other problems as well:
[ATTACH=CONFIG]275841[/ATTACH]

Some buttons and login boxes are black and what you write in the box can only be seen if you highlight it, however Google and startpage.com is not affected.

---

### Post by vasa1 on 2017-07-02
> **ardouronerous said:**
> ..., but it also caused other problems as well:
...

Some buttons and login boxes are black and what you write in the box can only be seen if you highlight it, however Google and startpage.com is not affected.

Is it possible to post all the issues in the first post itself along with some context? There's mention of a dark theme but the image you provided has a lot of white. So where's the dark?

---

### Post by ardouronerous on 2017-07-02
I'm using Windows 10 Dark from B00merang: [http://b00merang.weebly.com/windows-10-transformation-pack.html](http://b00merang.weebly.com/windows-10-transformation-pack.html)

---

### Post by vasa1 on 2017-07-03
> **ardouronerous said:**
> I'm using Windows 10 Dark from B00merang: [http://b00merang.weebly.com/windows-10-transformation-pack.html](http://b00merang.weebly.com/windows-10-transformation-pack.html)

Maybe contact the developers of that theme?

If you were using a theme from the software center, people may have been able to help.

---

### Post by ardouronerous on 2017-07-03
I don't think it's a problem with the theme, I've read Firefox has had this problem for a long time now with dark themes, leading to people using userContent.css to fix the problem.

---

### Post by vasa1 on 2017-07-03
Let's try one thing at a time. Starting with the userContent.css you modified as per my earlier post, change ```
input {
border: 2px inset white;
background-color: white;
color: black;
}
```to```
input {
border: 2px inset white;
background-color: white !important;
color: black !important;
}
```and see if anything changes when you restart the browser.

---

### Post by ardouronerous on 2017-07-03
No change, same problem like post # 5.

After Googling the issue, I discovered this thread: [https://forums.gentoo.org/viewtopic-p-8082448.html?sid=29507bcf45cec4d44bf43752c77b72ea](https://forums.gentoo.org/viewtopic-p-8082448.html?sid=29507bcf45cec4d44bf43752c77b72ea)

[QUOTE=Saundersx]The userContent.css was also the issue for me but  it's wasn't a complete solution to my problem as the GTK dark themes  were running havoc again. However I found this extension [https://addons.mozilla.org/en-US/firefox/addon/text-contrast-for-dark-themes/](https://addons.mozilla.org/en-US/firefox/addon/text-contrast-for-dark-themes/) which is a much better solution. Other solutions can also be found here [https://wiki.archlinux.org/index.php/Firefox#Unreadable_input_fields_with_dark_GTK.2B_themes](https://wiki.archlinux.org/index.php/Firefox#Unreadable_input_fields_with_dark_GTK.2B_themes)[/QUOTE]

So I installed the Firefox add-on Text Contrast for Dark Themes as indicated by Saundersx, and it works like a charm, eliminating the need for userContent.css.

---

