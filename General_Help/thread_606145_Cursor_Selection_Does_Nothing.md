---
title: "Cursor Selection Does Nothing"
date: 2007-11-07
forum: General Help
---

### Post by OzzyFrank on 2007-11-07
Hmmm... when I open **System > Preferences > Cursor Selection**, I can't actually seem to do anything with it. All I can do is select the different themes in the list, and that's it. At first I figured selecting them didn't change the theme maybe coz of shadows that my system can't handle at the moment (I'm being forced to run the "vesa" graphics driver since the Gutsy upgrade destroyed the "ati" driver). But when I click **"Install Theme"** it does nothing... and even** "Go To Theme Folder"** does absolutely nothing.

Has anyone else experienced this? Does anyone know how to fix this?

---

### Post by blakcode on 2008-07-18
Bump, yes I am having the exact same problem, did you ever get yours to work?

---

### Post by OzzyFrank on 2008-07-18
Go to **System > Preferences > Appearance > Theme** and click the **Customize** button. then go to the **Pointer** tab. All installed themes will be there. I'm pretty should I could change them there before, but now can't due to what I suspect is having Compiz-Fusion running. To install the themes, just drag the archives containing them to the **Appearance Preferences** box and it will be installed like a Metacity or icon theme.

Ok, just figured out how to get Compiz to let go of handling the cursor. In **System > Preferences > Advanced Desktop Effects Settings** go to **General Options > General** you will see the **Cursor theme** field with the name of the current theme, eg: *human*. There is no way to pick a new one from there, but you can type it in. Alternatively, you can try the recycle bin button at the end of it, which will **Reset setting to the default value**. The name of the theme in the field will then disappear. For me, suddenly the cursor theme I had tried to initiate under **Pointer** took over from the *human* theme specified in Compiz. However, it didn't seem to last for long, as it is back to the default *human* theme again, hehe.

Just realised it always shows the plain default cursor over the browser I am using, Opera, but checking again I cannot change the cursor from **Pointer**. However, typing or pasting the name of the cursor, which is the name of the folder it lives in under **/home/yourname/.icons** (you will need to have **Show Hidden Files** enabled in Nautilus) does the trick.

So if you're not using Compiz-Fusion, you should just be able to go to **Pointer** under **Appearance**. To install, drag the .tar.gz file onto **Appearance Preferences** or just unzip them in the **.icons** folder.

If using Compiz, you may need to copy the name of the theme folder in **~/.icons** and paste it next to **Cursor theme**. This will work on GTK apps, but others like Opera will show a plain default theme. Same goes for KDE apps you might have installed. And of course Windows apps running under Wine.

Interesting footnote: There is one app I just noticed is running the cursor theme that is specified in **Pointer**, and it isn't a Gnome app as such, but is **Mozilla Thunderbird** email client. Just fired up **Firefox** and sure enough it is using it too. And when I change the theme in **Pointer**, the Mozilla apps take note. All the Gnome apps are using the one specified in Compiz-Fusion.

And lastly, don't be surprised if it looks like you've basically got a cross between 2 themes running, as I was trying to figure out why the other cursors beyond the pointer (ie: text-insertion cursor etc) didn't seem to fit. The main pointer is what I have specified in Compiz, but everything else belongs to the theme specified under **Pointer** in **Appearance Preferences**. Weird how the Mozilla apps show the whole theme and disregard the Compiz setting, but Gnome apps show a hybrid.

Just fired up another Gnome app, **gLabels**, and when I actually used the text cursor to select some text, suddenly the Compiz-specified pointer reverted to the one in the other theme. Close it down and reopen it, back to the way it was until I use the text cursor again.

Anyway, with all that info, hopefully I've covered everything, so anyone reading this will be able to change their themes, and the main pointer via Compiz if need be. Cheers

---

### Post by OzzyFrank on 2008-07-21
_[COLOR="Red"]**Update:**[/COLOR]_ Seems rebooting makes a difference, as **Opera** and my **KDE** apps now use the full theme as specified in A**ppearance > Customize > Pointer**. Gnome apps still use a hybrid, being the main pointer cursor as specified in Compiz + the rest of the cursors from the theme specified in **Pointer**. Windows apps in Wine still show a basic default theme, but that is to be expected, I suppose.

---

