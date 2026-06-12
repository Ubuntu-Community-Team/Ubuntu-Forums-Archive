---
title: "How can i customise panel/dock"
date: 2018-09-04
forum: General Help
---

### Post by 8h567t20 on 2018-09-04
Hello can some one tell how i can the panel/dock a bit darker. I have tried to change the theme with gnome tweak tools but i cant any thin to with the themes i have changed  applications to arc-darc icons to Matcha.

---

### Post by deadflowr on 2018-09-04
Whie I'm sure there's a simple method to do this I always set a custom theme file that does it fairly simply.
You need to create a .themes folder in your home folder (the dot is crucial as the folder needs to be hidden)
Create a theme file called anything you want, like My-custom-theme.
Then create a folder inside it called gnome-shell
the create a file inside that called gnome-shell.css
in the file place this
```
@import url("/usr/share/gnome-shell/theme/gnome-shell.css");

#panel {
    background-color: black;
    background-color: rgba(0,0,0,1.00); 
    font-weight: bold;
    height: 1.50em;
}
```
and save it.
now you need to install the gnome shell extension user-themes (if not already installed)
And then in the program Tweaks (also needs to be installed) enable the user themes extension, 
and go to Shell in the Themes section and you should see a toggle option dropdown with it marked Default.
You can toggle the theme here and select your new theme.
The change should be automatic.

The basic concept of the file above is it will change only one specific thing, and that will be the panel opacity.
The default opacity is something like 0,0,0,0.35,  where 0.35 is the opacity level of the alpha channel.
the output I posted gives the alpha channel full opacity. (0, 0, 0, 1.0 would be full opacity, black

This is a very basic override.
And the  fun of it is you can also play around with any other shell theme setting here, found inside the file that's listed in the @import line in the file.

As I posted to begin with there is probably an easier way, but I like this way as it is very simple.


Edit: You can change height to whatever you want, I forgot that's what I set mine to, and I don't think it's the default.
I think the default are
```

height: 1.83em;
```

hope it clears that up.

---

### Post by 8h567t20 on 2018-09-04
For some resone every time i leave tweaks the and open it again it say (none) in the place i but it and it says gnome tweaks crashde

thanks i found a fixi just rebboted tryde again and i workde thanks for helping me.

---

### Post by ajgreeny on 2018-09-04
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

