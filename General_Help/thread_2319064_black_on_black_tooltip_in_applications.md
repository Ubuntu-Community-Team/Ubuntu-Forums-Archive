---
title: "black on black tooltip in applications"
date: 2016-03-31
forum: General Help
---

### Post by ineuw on 2016-03-31
How can I correct black characters on a black background in applications' tooltips. I found the solution for the desktop with the following code, placed in my .gtkrc-2.0 file, and this works. But I still get some applications like Firefox with the same problem. I was sure that tooltips are control by xfce and not by an application.

```

style "custom-tooltip"
{
  bg[NORMAL] = "#000000"
  fg[NORMAL] = "#ffffff"
}
widget "gtk-tooltips" style "custom-tooltip"

```

---

### Post by Dennis N on 2016-03-31
In Greybird I have equal settings in these locations that match the tooltip colors. Did you check both places for your theme? But, I believe some applications might override these.

/usr/share/themes/Greybird/gtk-2.0/gtkrc contains:
```
gtk-color-scheme	= "tooltip_bg_color:#000000\ntooltip_fg_color:#E1E1E1" # Tooltips
```
/usr/share/themes/Greybird/gtk-3.0/gtk.css contains:
```
@define-color tooltip_bg_color #000;
@define-color tooltip_fg_color #e1e1e1;
```

---

### Post by ineuw on 2016-03-31
Thanks Dennis N. I found them and changed both fg  (#e1e1e1; )  to #ffffff; just to see if it works, but there is no change. The culprit is Firefox but Thunderbird is as defined. I posted a similar post in Mozillazine, and now will look for myself in about:config. Thanks again.

---

### Post by vasa1 on 2016-03-31
> **ineuw said:**
> ... But I still get some applications like Firefox with the same problem. ...

Firefox 45 has more than one type of tooltip. I have the following and I'm not claiming the list is complete:
[LIST]
[*]#main-window > tooltip
[*]#tabbrowser-tab-tooltip
[*]#aHTMLTooltip
[*]#bhTooltip
[/LIST]
I will revisit Firefox's tooltips after I move to 16.04 because by then Firefox will (probably) be using gtk3 and not gtk2. (Even now, Firefox 46 (beta) uses gtk3 but my gtk3 is version 3.10 and 16.04 will bring in gtk 3.18.)

---

### Post by ineuw on 2016-04-01
> **vasa1 said:**
> #main-window > tooltip

[*]#tabbrowser-tab-tooltip

[*]#aHTMLTooltip

[*]#bhTooltip


Thanks vasa1, you gave me plenty of food for thought. Where are those FF tooltips you mentioned?

---

### Post by vasa1 on 2016-04-01
> **ineuw said:**
> Thanks vasa1, you gave me plenty of food for thought. Where are those FF tooltips you mentioned?
I have them in a Stylish sheet. [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/stylish/") is an extension for Firefox (and some other browsers) that allows you to customize the appearance of various aspects of Firefox. One could also write styles directly in userContent.css and userChrome.css but using Stylish allows you to see the effect without having to restart Firefox.

Stylish has its support webpage at userstyles.org and a forum as well at forum.userstyles.org.

With that as background, here's part of a stylesheet I have to show the various tooltips:

```
/* AGENT_SHEET */ 

@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

#main-window > tooltip { color: #777777 !important }
#tabbrowser-tab-tooltip { color: #777777 !important }
#aHTMLTooltip { color: #01080F !important; background-color: red !important; }/*  post summary on UF pages; background-color doesn't work; seems to be set in gtkrc */
#bhTooltip { color: #777777 !important; border: none !important; } /* text color on hover over items in bookmark bar*/
```

I too use Greybird, modified somewhat, as my gtk2 theme. In there, I have:```
gtk_color_scheme	= "tooltip_bg_color:#333333\ntooltip_fg_color:#888888" # Tooltips.
```

As I said, I don't want to spend more time on customizing Firefox's appearance because it will become a gtk3 app in version 46 and something may change ;)

---

### Post by Dennis N on 2016-04-01
> I found them and changed both fg (#e1e1e1; ) to #ffffff; just to see if it works, but there is no change.

You might not be noticing the change - e1e1e1 is an off-white and very close to FFFFFF. To see if and how those theme settings affected Firefox, I changed mine in both places mentioned, to F1E569 (light-yellow) and Firefox tool tips changed text color immediately. I only see the one tool tip text color on FF tabs, FF links, FF toolbar and in the FF main window, so I suspect the default on FF tool tips is to use same colors for all. The XFCE panel will not change until you log out and log in, but it picks up the same text color for tool tips.

I like the yellow. Think I will leave it so.

---

### Post by ineuw on 2016-04-01
Thanks to both of you for the info. I was aware that there is not much difference between the two whites, but nothing changed. Still black on black, so I will check the userContent.css because adding to userChrome.css didn't do anything.

---

### Post by Dennis N on 2016-04-01
You did not mention which theme you  are using. Perhaps one of us could try that theme, confirm your observations, and possibly find a fix.

---

### Post by ineuw on 2016-04-01
Apologies, I am using Greybird, which I believe is the default setting.

---

### Post by vasa1 on 2016-04-02
In your other thread, you've mentioned you're on Fx 46 beta. That's gtk3, isn't it? At least my Fx 46 beta is.

---

### Post by ineuw on 2016-04-02
Yes. Believe I changed both 2 and 3  but will check tomorrow morning, unless I get a second wind.

---

### Post by Dennis N on 2016-04-02
> **vasa1 said:**
> In your other thread, you've mentioned you're on Fx 46 beta. That's gtk3, isn't it? At least my Fx 46 beta is.
This should have been mentioned up front. There has to be another factor involved in the system to cause the black text problem, since I for one can't duplicate it in the FF 45.0.1,  using the same theme (Greybird).

---

### Post by Dennis N on 2016-04-02
If it is true that you are using a Firefox version still under development, have you tried reverting to the current Firefox release version from the Ubuntu repositories? Possibly your theme problem may go away. Another useful thing to know is when this problem first appeared. Was it there at the time of installation? Did you make some change in your system and then noticed it? If so, and you can pinpoint what you did, you can possibly reverse it.

---

### Post by vasa1 on 2016-04-02
> **Dennis N said:**
> If it is true that you are using a Firefox version still under development, ...
> I am using the default FF theme, although I am using FF 46.5b, which should not make a difference. Also, the Xubuntu theme is the default Greybird, I believe it's called. Presently I am in Windows, so I can't check the exact name.from [http://forums.mozillazine.org/viewtopic.php?p=14561543#p14561543](http://forums.mozillazine.org/viewtopic.php?p=14561543#p14561543)

---

### Post by Dennis N on 2016-04-02
@vasa1

Read that linked thread. First post says it the problem existed "on installation" (so on the repo version of FF as well?). Again, that should have been conveyed here as well. I don't see any link to that thread besides yours, so I'm wondering where you got it.

Reading that other thread (which has no solution) - not clear to me what Grumpus is talking about "Three tabs Theme, Background and Fonts.."? I see nothing like that in Xubuntu. The theme-writer Frank Lion's comment: "Not going to be Firefox default theme, as that uses OS for tooltips." is what I see as well (OS theme settings for tooltips). 

I don't use Firefox's default theme, but when I revert to it, I see no problems with tooltips there. Some key fact is still not evident. Will check again at a later time.

---

### Post by vasa1 on 2016-04-02
> **Dennis N said:**
> @vasa1

Read that linked thread. First post says it the problem existed "on installation" (so on the repo version of FF as well?). Again, that should have been conveyed here as well. I don't see any link to that thread besides yours, so I'm wondering where you got it.

Reading that other thread (which has no solution) - not clear to me what Grumpus is talking about "Three tabs Theme, Background and Fonts.."? I see nothing like that in Xubuntu. The theme-writer Frank Lion's comment: "Not going to be Firefox default theme, as that uses OS for tooltips." is what I see as well (OS theme settings for tooltips). 

I don't use Firefox's default theme, but when I revert to it, I see no problems with tooltips there. Some key fact is still not evident. Will check again at a later time.

I visit that forum and so it wasn't difficult to find. OP used the same login name there.

I rarely understand posts made by Grumpus :(

The bit about Firefox default theme ... the OS theme, Greybird in this case, is the same as the Firefox default theme unless one installs another Firefox theme which should then be selected in Tools, Addons, Appearance. It's been quite a while since I used another Firefox theme. There's then a chance of clashes between the Firefox theme and the gtk theme.

---

### Post by ineuw on 2016-04-02
To be honest I also cross-posted this issue to Mozillazine where I also sought help. Changed the about:config setting 'browser.display.use_system_colors' to 'true' and this didn't do anything. But, when I changed the Xubuntu 'Appearance/Style' to 'Raleigh', the tooltip changed to creamy yellow background with black letters everywhere, including Firefox, but Thunderbird remained white foreground on black background as it was with 'Greybird'. I will try to track this down and figure out what's wrong with Greybird. Much thanks to you all for the help.

---

### Post by vasa1 on 2016-04-02
Not strictly related but since there was mention of Firefox themes: [How do I set Firefox to use a custom theme for all new users?]("http://askubuntu.com/questions/743903/how-do-i-set-firefox-to-use-a-custom-theme-for-all-new-users")

---

### Post by Dennis N on 2016-04-03
> **vasa1 said:**
> Not strictly related but since there was mention of Firefox themes: [How do I set Firefox to use a custom theme for all new users?]("http://askubuntu.com/questions/743903/how-do-i-set-firefox-to-use-a-custom-theme-for-all-new-users")

And now we have 'themes' and 'complete themes' in Firefox to confuse the issue a bit. I use only a Firefox 'theme', which used to be called a 'Persona'. These also work in LibreOffice - I use one. The folder for themes in L.O. gallery is still called 'Personas'.

I wonder if the Firefox 'complete themes' work in L.O?

---

### Post by vasa1 on 2016-04-03
> **Dennis N said:**
> ... I use only a Firefox 'theme', which used to be called a 'Persona'. These also work in LibreOffice - I use one. ...
Would you please post an image of LibreOffice Calc with and, if possible, without the persona/theme? What aspects of the user interface are themed this way?

---

### Post by Dennis N on 2016-04-03
> **vasa1 said:**
> Would you please post an image of LibreOffice Calc with and, if possible, without the persona/theme? What aspects of the user interface are themed this way?

Yes, here is screen shot attached - L.O. calc (5.0.5) with 'theme' (Persona) called "Gray and white gradient". I used the same 'theme' on Firefox. Icons in L.O. of course are not system icon theme - they are its Tango icon theme as you may recognize. 

You can try them out without installing by going to the 'themes' page. Then, just hover over a theme image to apply it temporarily. What is changed can vary.  

[https://addons.mozilla.org/en-US/firefox/themes/](https://addons.mozilla.org/en-US/firefox/themes/)

Sorry - can't show the default as it might not be straightforward to return to what I want. Using the L.O. theme search tool gave me problems getting this theme to come up in a search, and I found no way to select a theme that is already in the Persona folder using the tool. In the end, I copied it from another L.O. install, and manually edited the .config file in L.O.

But, the default is just a flat grey background.

---

### Post by vasa1 on 2016-04-03
Thank you :)

I'm just using Greybird which I've modified to be darker overall. I've also reduced the rows occupied by the UI by removing icons I don't use or which have easily accessible keyboard shortcuts. The only thing I don't like about my color scheme is the way the row and column headers appear half bright and half dark. And I have no idea how to fix that :(

---

