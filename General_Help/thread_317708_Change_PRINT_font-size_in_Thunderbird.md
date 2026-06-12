---
title: "Change PRINT font-size in Thunderbird"
date: 2006-12-12
forum: General Help
---

### Post by altonbr on 2006-12-12
I just setup Ubuntu on my grandmothers computer, but she keeps complaining about the size of the printed font as being to small. The original reason why I actually switched her from Outlook Express/Windows to Mozilla Thunderbird/Ubuntu was for this very reason. Outlook Express is integrated into Internet Explorer and it was hard as hell to try and change the font-size in IE. The whole process was convoluted, so I gave up.

NOW, the same darn thing is happening. You can only change the DISPLAY size for fonts, but prints the default. I heard that you can create a css file in ~/.mozilla-thunderbird/*<alphanumeric account name>*/chrome/userContent.css .. and it worked, but it was for display again, and not printing.

Does anyone know a solution?

She uses an old Canon BJC-1000. Is there a way to increase the size of the font before it goes to post-script (or after), through the printer settings (or CUPS)?

Thanks!

---

### Post by al_sharpe on 2006-12-13
Hello altonbr:

To increase font size in Thunderbird printing easily
File --> Page Setup
and uncheck Shrink To Fit Page Width and change scale to say 125
(larger if need be)
The setting stays when Thunderbird shuts down and is restarted,

Simple eh

Al Sharpe

---

### Post by altonbr on 2006-12-13
Yes, that makes sense, as it's the same as Firefox, but I don't find it that logical. I think most people would be looking for "Font Size: 16px" not "Scale: 125%". This is because what if you get an e-mail that is 12px and you want it 16px, but another you get at 20px and you want it at 16px. That means that every time you want to print a document, you'll have to change those settings [-( .

Thanks for the advice though!

I'll take my argument to Mozilla.

---

### Post by Bingulim on 2007-05-07
I agree with altonbr. This is not easy to make a trace to.
And to be honest, the results are a little away from what I was expecting, but it works.

What I personally do is convert my e-mail to PostScript (Print->PostScript option instead of printer), than I print it. Its contra-effective, but if you nedd a good printed e-mail, that is a away to go.

---

### Post by altonbr on 2007-05-12
Well, 5 months later, Mozilla Thunderbird 2.0 comes out, and you still can't set a fixed font-size. I don't mean monospace font, I mean to have ALL fonts that are below 14px to be bumped up to 14px or anything about to be bumped down.

Current options (but not ripe for seniors):
[LIST]
[*]hit 'ctrl plus +' on every message [only for display]
[*]change print size at every print [too much work and tinkering]
[*]custom CSS in the chrome [only display, not working in Thunderbird 2.0]
[/LIST]

In "Edit > Preferences...> Display > Fonts..." is has a 'minimum font size' but it's clearly not working. I have every set at 16px, and my Grandmother still receives e-mails at 10px or smaller.

---

### Post by altonbr on 2007-05-12
Plus, Thunderbird 2.0 is ignoring my ~/mozilla-thunderbird/<alphanumeric string>/chrome/userContent.css file.

It currently looks like this:

> *{
	font-size: 16px !important;
}


I'm a Web Developer and I know that should work (as it did for Thunderbird 1.5).

---

### Post by altonbr on 2007-05-19
Any ideas?

---

### Post by altonbr on 2007-05-21
I backed up my 'Mail' folder, wiped everything else out in my preferences and then pasted my 'Mail' folder back in  once I set up my account again. This got rid of any inconstancies between 1.5 and 2.0 but the font size is still looking quite odd. I had to make the font size 20px before it became 14px on screen using that CSS style sheet in the 'chrome' folder. So now I have to make the print layout 85% instead of 120% like before.

I guess this is a stiff warning to keep your software within the repositories and not compile from source.

Everyone says wait for Gusty, but that's a little ridiculous I think since Windows users and download and install Thunderbird 2.0 at will. Ubuntu users have to wait until October 2007 for it to be official supported, a full 5 months from now.

Anyways, I'll downgrade Thunderbird and Firefox back to 1.5 for now...

---

