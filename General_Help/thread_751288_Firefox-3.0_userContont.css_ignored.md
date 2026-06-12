---
title: "Firefox-3.0 userContont.css ignored"
date: 2008-04-10
forum: General Help
---

### Post by Jive Turkey on 2008-04-10
Firefox 3.0.5 Beta boasts a new troubling "improvement":
"[Improved in Beta 5!] Integration with Linux: Firefox's default icons, buttons, and menu styles now use the native GTK theme."

I don't know for sure if this has anything to do with it the userContent.css fix for dark themes seems not to work anymore.  Maybe I need to change it some more I don't know.  

My userChrome.css:
```
 

input, textarea {
	border: 2px inset white;
	background-color: white;
	color: black;
  border: 1px solid #aaa;
}

select {
	border: 2px inset white;
	background-color: white;
	color: black;
}
 
input[type="radio"],
input[type="checkbox"] {
	border: 2px inset white ! important;
	background-color: white ! important;
	color: ThreeDFace ! important;
}

*|*::-moz-radio {
	background-color: white;
}

button, 
input[type="reset"],
input[type="button"],
input[type="radio"],
input[type="submit"] { 
	border: 2px outset white ! important;
	background-color: #eeeeee ! important;
	color: black ! important;
}

body {
	background-color: white;
	color: black;
	display: block;
	margin: 8px;
}

```

Any thoughts?  This used to make pages more readable for me in ff-2.  Yes I'm on hardy but this is a FF issue.  I'd like to give the FF developers some feedback on this matter but I'm not sure where to do that.

---

### Post by Mindless Automata on 2008-04-10
I was just looking for a fix for this, too.  Anyone?

---

### Post by Mindless Automata on 2008-04-12
...nobody?

---

### Post by Ryuki_NdranC on 2008-04-22
I was lookin for this too :) but i figured no one yet have made one. Im still dep googleing for this, if i find something i will post here.

Good luck

---

### Post by kingkookie on 2008-05-11
I just had a similar issue while doing web development.  Using an external css outside of my php file, I first defined the body style:

[FONT="Courier New"]body {
 background-color: #000000;
}[/FONT]

Then went on to define other attributes.

Only, the body style was being completely ignored.  If I copied my entire stylesheet into my php file, everything worked, but embedding an external css file resulted in the body style being ignored.  

I discovered, that it was not the body style specifically that is being ignored, but it's the first style at the top of the list that is being ignored.

I worked around the problem by creating an empty style:

[FONT="Courier New"].ignored {

}[/FONT]

This problem occurs in both Konqueror and Firefox 3.0.  Have not tested in IE or earlier versions of Firefox, but it's been frustrating to figure out what was wrong.

Hopefully that helps with this issue.

---

### Post by Jive Turkey on 2008-05-15
For now I'm just using FF2, and Opera, I might not use ff at all once v2 drops off the radar.

---

