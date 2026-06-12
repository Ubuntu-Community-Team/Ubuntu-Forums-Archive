---
title: "can't see typed input in firefox"
date: 2018-08-19
forum: General Help
---

### Post by babag on 2018-08-19
using ubuntu 18.04 lts and xfce 4.12. also using dark theme. when i type input into a forum input field (not this forum) the field bg is dark gray and so, apparently, is the text as i can't see the typing at all. on this forum the input field appears white so there's no problem. how can i address this so i can see my input as i type? as it is, i have to stop typing and select-all to see what i've done so far.

thanks for any insight.
BabaG

---

### Post by tea for one on 2018-08-19
> **babag said:**
> using ubuntu 18.04 lts and xfce 4.12. also using dark theme. when i type input into a forum input field (not this forum) the field bg is dark gray and so, apparently, is the text as i can't see the typing at all. on this forum the input field appears white so there's no problem. how can i address this so i can see my input as i type? as it is, i have to stop typing and select-all to see what i've done so far.

thanks for any insight.
BabaG

Good evening

I found a theme on [www.gnome-look.org](www.gnome-look.org) where one of the comments gave an instruction to create a new folder in your firefox default profile:-

> You create folder "chrome" with "userContent.css" file. Look at this path:
/home/USER/.mozilla/firefox/??????????.default/chrome/userContent.css

Here is the userContent.css:-

```
/*
* Use this css file to eliminate problems in Firefox
* when using dark themes that create dark on dark
* input boxes, selection menus and buttons. Put this
* in the ../firefox/default/chrome folder or your
* individual user firefox profile chrome folder.
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

Now, I understand if you are a bit reluctant to use some random code from an unknown source but I have been using this with Vimix-Colour-Dark-Ruby theme for more than 4 months and it is working OK.

Secondly, the new folder **chrome** is under your control in your Home directory, therefore, if it gives you some problems, you simply delete it, restart Firefox and you are back to square one.

Kind regards

---

### Post by babag on 2018-08-22
thanks! i'll give this a try.

BabaG

---

