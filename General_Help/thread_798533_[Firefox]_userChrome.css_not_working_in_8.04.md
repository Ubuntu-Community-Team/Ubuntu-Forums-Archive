---
title: "[Firefox] userChrome.css not working in 8.04?"
date: 2008-05-18
forum: General Help
---

### Post by dpm_edinburgh on 2008-05-18
Hi.

  I have a bizarre problem in Ubuntu 8.04.  Basically, I have a gnome theme installed that makes all my menubars a brown colour, with whitish text.  The menus also have quite a bit of padding, so the text is easy to read.  This is consistent across all applications, apart from Firefox (this by the way, seriously ****** me off---all applications should look the same---argh!)

  So, I tried to customize firefox myself, by taking the userChrome-example.css file and editing it, saving it as userChrome.css.  The file is saved in ~/.mozilla/firefox/81e67q2l.default/chrome, and that's the only profile directory that I have.

  However, no matter what entries I put into the userChrome.css file, firefox still looks exactly the same!  It's as if the file is being ignored completely.  I thought maybe I was putting the wrong entries in, so I went online and found some standard ones (i.e. hiding the Help menu) but none of those work either (of course, I restarted firefox to test).

  Does anybody know what is wrong?  All I want to do is increase the padding around the menubuttons on the main menu and change the colour of those buttons from black to white.

TIA.

---

### Post by dpm_edinburgh on 2008-05-18
Bump?

---

### Post by kalibar on 2008-06-23
> **dpm_edinburgh said:**
> Bump?
I saw this thread and my eyes lit up because I was hoping to see a resolution.  This is happening for me too, Firefox is completely ignoring my userChrome.css file -- this is driving me particularly crazy because I'm trying to perform the [Bookmarks Toolbar folder dropdown arrow removal as outlined here](http://brainstorm.ubuntu.com/idea/7722/).

---

### Post by salamander113 on 2008-09-20
I've the same problem and there doesn't seem to be a solution yet.

---

### Post by TeXtonyx on 2008-10-08
Hi, 
I just posted a response which included userChrome.css information.
I'm not going to edit it, but it works as I can see while I type this message.
Maybe you have the syntax wrong with the brackets. Anyway, it should 
prove to you that userChrome.css is read and acted upon by Firefox. 
Did you know that there is another file called userContent.css which 
does something similar to userChrome.css? Since I show that userChrome.css
works, it means the problem is in your code or your choice of config file.

Mainly I'm saying I doubt it is a Firefox problem. For instance I created
a Downloads folder for Firefox downloads. But I could never download any
files to the Downloads folder. It turned out I had made the Downloads folder
with sudo so that my regular username downloads didn't have the permissions
required to write to the Download folder. So there can me many reasons.
Actually you can test your setup using just my userChrome.css file. If it
doesn't work then you know the problem is not your syntax, or choice of
config file, or Firefox, but more of a Ubuntu related profile/permission 
issue. If my file does work for you, then it isn't a Firefox or Ubuntu bug. 

Begin content of other post (8.04) re: userChrome.css \/\/\/

"The reason I posted my userChrome.css file is that
Preferences will not make all the fonts larger that a visually
impaired person needs larger. Just change
the numbers next to mm, such as 4.5mm or 5mm or 5.5mm

Here is a copy of my userChrome.css
------------------------------------------->

window {
font-size: 5mm !important;
font-family: Adobe Caslon Pro Bold !important;
}

menubar, menubutton, menulist, menu, menuitem {
font-family: helvetica !important;
font-style: italic !important;
font-weight: bold !important;
font-size: 4.5mm !important;
}

----------------------------------------->

The xxxxxxxx will be unique letters/numbers identifying your profile.
Copy and paste the content *between* the dotted lines.
This belongs in the chrome directory and you will most likely
need to make the chrome folder with mkdir or the file browser.

/home/username/.mozilla/firefox/xxxxxxxx.default/chrome/userChrome.css

/home/username/.mozilla-thunderbird/xxxxxxxx.default/chrome/userChrome.css

To see dot files, . , you need ls -la from the command line or turn on
'Show hidden files' which is under View in the file browser. I have
fixed this problem for a hard of seeing customer which is why I
think this step is needed additionally to setting Preferences,
depending of course on the degree of visual difficulty."

---

### Post by TeXtonyx on 2008-10-08
This is a sample userContent.css file I found that looks more appropriate to me than userChrome.css Also under 
Edit-> Preferences-> Colors, "Allow pages to user their own colors instead of my selections above" might work better than ticking the box "use system colors".

[http://ubuntuforums.org/archive/index.php/t-541329.html](http://ubuntuforums.org/archive/index.php/t-541329.html)

Here are some dark themes. They should all be available at gnome-look.org.

46165-Clearlooks_blackblue.tar.gz
46238-MurrinaBlackBlue.tar.gz
54166-Murrina-Neutronium_DeepBlack.tar.gz
63549-GTK-BlueGlow.tar.gz

And here is my userContent.css:


/*
* Edit this file and copy it as userContent.css into your
* profile-directory/chrome/
*/

/*
* This file can be used to apply a style to all web pages you view
* Rules without !important are overruled by author rules if the
* author sets any. Rules with !important overrule author rules.
*/

/*
* example: turn off "blink" element blinking
*
* blink { text-decoration: none ! important; }
*
*/

/*
* example: give all tables a 2px border
*
* table { border: 2px solid; }
*/

/*
* example: turn off "marquee" element
*
* marquee { -moz-binding: none; }
*
*/

/*
* For more examples see [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)
*/

textarea, input {
color: #000 !important;
background-color: #fff !important;
}

/* Single line text fields */
input {
/* Set font size and family of text fields */
font-family: clean !important;
font-size: 13px !important;

/* Set background color to something a little prettier
background-color: rgb(200, 255, 220) !important; */

/* Add some key bindings.
* For an explanation of how to do this,
* see below under "Custom key bindings".

-moz-binding: url("resource:///res/builtin/myHTMLBindings.xml#myInputFields") !important;
}*/


/* The dropdown address and autocomplete windows are grey.
* To make them match better with the URL field and look more like 4.x:
*/

/* URL dropdown box
#ubhist-popup
{
background : white !important;
border : 1px solid black !important;
padding : 0px !important;
}
* autocomplete text field */
.textfield-popup
{
background : white !important;
border : 1px solid black !important;
}*/

#ubhist-popup > .popup-internal-box, .textfield-popup > .popup-internal-box
{
border-left : 1px solid white !important;
border-top : 1px solid white !important;
border-right : 1px solid white !important;
border-bottom : 1px solid white !important;
}
textarea {
min-width: 50ex !important;
min-height: 12em !important;
color: #000 !important;
background-color: #fff !important
}
slider {
height: 20px !important;
color: #fff !important;
background-color: #000 !important
}
slider[align="vertical"] {
width: 20px !important;
}
select, option {
color: #000 !important;
background-color: #fff !important
}

---

