---
title: "How can I create a transient notification on-screen?"
date: 2020-12-12
forum: General Help
---

### Post by Paddy Landau on 2020-12-12
I can use [FONT=courier new]notify-send[/FONT] to display an on-screen message.

[LIST]
[*]With [FONT=courier new]--urgency=low[/FONT] or [FONT=courier new]--urgency=normal[/FONT], the message disappears from view after 4 seconds, but it remains in the history (when you click the clock at the top) until manually dismissed.
[*]With [FONT=courier new]--urgency=critical[/FONT] , the message remains on-screen until manually dismissed.
[/LIST]
There's a third option that [FONT=courier new]notify-send[/FONT] doesn't seem to support. I've seen messages by some apps display on-screen and disappear by themselves, but they **don't** remain in the history. Once they disappear, they've gone forever. For example, the Gnome extension [Lock Keys]("https://extensions.gnome.org/extension/36/lock-keys/") does exactly this &#8212; there's no need to keep a historical record of how often you've pressed Caps Lock.

I want to do the same thing for certain messages, and I can't figure out how. The option [FONT=courier new]--expire-time[/FONT] is ignored in Gnome, so that doesn't help. There obviously is an alternative on-screen notification command that looks like [FONT=courier new]notify-send[/FONT] but allows for transient messages. What is it?

I'm using standard Ubuntu 20.04, which has Gnome 3.36.3.

Thank you

---

### Post by #&amp;thj^% on 2020-12-12
I've used the lines as described here:[https://askubuntu.com/questions/868474/show-notify-send-content-in-gnomes-lockscreen](https://askubuntu.com/questions/868474/show-notify-send-content-in-gnomes-lockscreen)
I know it works 20.04

---

### Post by sudodus on 2020-12-12
You can do it with zenity.

I don't think you can control the time with [FONT=Courier New]**--notification**[/FONT], but you can with [FONT=Courier New]**--info**[/FONT]. Try and tweak

```

zenity --info --text="zenity can do it for you" --no-wrap --timeout=2

```

---

### Post by #&amp;thj^% on 2020-12-12
> **sudodus said:**
> You can do it with zenity.

I don't think you can control the time with [FONT=Courier New]**--notification**[/FONT], but you can with [FONT=Courier New]**--info**[/FONT]. Try and tweak

```

zenity --info --text="zenity can do it for you" --no-wrap --timeout=2

```
Nice!

---

### Post by sudodus on 2020-12-12
Nice to meet you again in this thread, 1fallen :-)

---

### Post by Paddy Landau on 2020-12-13
> **1fallen said:**
> I've used the lines as described here:[https://askubuntu.com/questions/868474/show-notify-send-content-in-gnomes-lockscreen](https://askubuntu.com/questions/868474/show-notify-send-content-in-gnomes-lockscreen)
Thanks, but that does absolutely nothing for me! I've copied the script exactly, and when I run it, nothing happens. No error is shown in the terminal. :(
> **sudodus said:**
> You can do it with zenity&#8230;
Thanks. I'm aware of Zenity, but I was hoping to use the notification method, because it doesn't grab focus from the current task.

However, your comment on Zenity made me think. I usually use Yad (a fork of Zenity, available in the standard repositories) because it's far more powerful. This is not an ideal solution, but it comes close.
```
#!/usr/bin/env bash

####################################################################################################
# notify-send-transient: Simulate a transient notification.
# It works like notify-send --urgency=low, but the notification doesn't appear in the history.
# Simply call with the message that you want to display.
####################################################################################################

function initialise
{
    set -u                                 # Catch uninitialised variables.
    local -ir NOTIFICATION_WIDTH=500       # Desired width of notification.

    # Find the screen width.
    local -ir WIDTH=$( xrandr --nograb --current |
                       grep -E --only-matching ' connected primary [[:digit:]]+' |
                       cut --delimiter=' ' --field=4
                     )

    # How wide is the dock? I don't know how to find this directly, so I've used the icon width
    # and added 22 (because that's what I measured). It won't be quite correct on other systems.
    local -ir DOCK_ICONS=$( gsettings get org.gnome.shell.extensions.dash-to-dock dash-max-icon-size )
    local -ir DOCK_WIDTH=$(( DOCK_ICONS + 22 ))

    # Calculate where to place the left of the notification in order to centre it in the non-dock area.
    declare -gir CENTRE_POINT=$(( ( WIDTH - DOCK_WIDTH ) / 2 + DOCK_WIDTH - ( NOTIFICATION_WIDTH / 2 ) ))

} # initialise

function displayTransientMessage
{
    local -r MESSAGE="${@}"                # Combine all parameters into a message.

    # Display the message: Time out, don't grab focus, show on top, stick on all desktops; send to background.
    yad --text-info -on-top --sticky --no-focus --skip-taskbar --undecorated --width=${NOTIFICATION_WIDTH}   \
         --posx=${CENTRE_POINT} --posy=1 --button='Dismiss!gtk-ok' --buttons-layout=center \
         --wrap --justify=center --fontname=normal --timeout=4 --fore=white --back=black   \
         --listen <<<"${MESSAGE}" &

} # displayTransientMessage

initialise
displayTransientMessage "${@}"
```
And then execute with:
```
notify-send-transient 'Please read this message before it disappears forever!'
```
I'd still like to know the proper way to do this, so my question isn't answered, but this will do as a workaround until I find the correct answer.

---

### Post by #&amp;thj^% on 2020-12-13
Yup, Gnome adds a new twist to your request. I've been away far to long to have an instant call to memory, so I had forgoten gnome's dos and don'ts.

This script is the original but the sound dl link is now "404" :Found here: [https://gist.github.com/John-Almardeny/04fb95eeb969aa46f031457c7815b07d/archive/5502b0060e2a88f3a843b1c5d92c60ad229d7d64.zip](https://gist.github.com/John-Almardeny/04fb95eeb969aa46f031457c7815b07d/archive/5502b0060e2a88f3a843b1c5d92c60ad229d7d64.zip)
It also Downloads everything needed

```
#!/bin/sh

# https://gist.github.com/John-Almardeny/04fb95eeb969aa46f031457c7815b07d
# Create a Notification With Sound with a Given Message and Time
# The Downloaded Sound is from Notification Sounds https://notificationsounds.com/

MSSG="$1"
TIME="$2"

# install wget if not found
if ! [ -x "$(command -v wget)" ]; then 
    echo -e "INSTALLING WGET...\n\n"
    sudo apt-get install wget
    echo -e "\n\n"
fi

# install at package if not found
if ! [ -x "$(command -v at)" ]; then
    echo -e "INSTALLING AT...\n\n"
    sudo apt-get install at
    echo -e "\n\n"
fi

# install sox if not found
if ! [ -x "$(command -v sox)" ]; then
    echo -e "INSTALLING SOX...\n\n"
    sudo apt-get install sox
    sudo apt-get install sox libsox-fmt-all
    echo -e "\n\n"
fi

# download the noti sound if this is first time
# add alias to the bashrc file
if ! [ -f ~/noti/sound.mp3 ]; then
    echo -e "DOWNLOADING SOUND...\n\n"
    touch ~/noti/sound.mp3 | wget -O ~/noti/sound.mp3 "https://notificationsounds.com/wake-up-tones/rise-and-shine-342/download/mp3"
    sudo echo "alias noti=\"sh ~/noti/noti.sh\"" >> ~/.bashrc
    source ~/.bashrc        
    echo -e "\n\n"
fi

# notify with the sound playing and particular given message and time
echo "notify-send \""$MSSG\"" && play ~/noti/sound.mp3" | at $TIME
```
I modified it with my own sound.mp3. (if further guidance is needed let me know)
I wonder if this will work for you, I use "Mate" here so your mileage may vary.
[list]Setting Up:

    [B][*]Create a new Directory at your home and call it noti

    [*]mkdir ~/noti

    [*]Download noti.sh and extract it to the above noti dir.

    [*]Open Terminal and Change Directory to noti

    [*]cd ~/noti

    [*]Make noti.sh executable by issuing:

    [*]sudo chmod +x noti.sh

    [*]Run a Test like this:[/list][/B]

    ```
sh ~/noti/noti.sh "Test" "now"

```
FWIW my (changed) script is as follows due to the broken download links for sounds: (any .mp3 should work just rename it.)
```
#!/bin/sh

# https://gist.github.com/John-Almardeny/04fb95eeb969aa46f031457c7815b07d
# Create a Notification With Sound with a Given Message and Time
# The Downloaded Sound is from Notification Sounds https://notificationsounds.com/

MSSG="$1"
TIME="$2"

# install wget if not found
if ! [ -x "$(command -v wget)" ]; then 
	echo -e "INSTALLING WGET...\n\n"
	sudo apt-get install wget
	echo -e "\n\n"
fi

# install at package if not found
if ! [ -x "$(command -v at)" ]; then
	echo -e "INSTALLING AT...\n\n"
	sudo apt-get install at
	echo -e "\n\n"
fi

# install sox if not found
if ! [ -x "$(command -v sox)" ]; then
	echo -e "INSTALLING SOX...\n\n"
	sudo apt-get install sox
	sudo apt-get install sox libsox-fmt-all
	echo -e "\n\n"
fi

# download the noti sound if this is first time

fi

# notify with the sound playing and particular given message and time
echo "notify-send \""$MSSG\"" && play ~/noti/sound.mp3" | at $TIME

```

---

### Post by norobro on 2020-12-13
First, thanks for mentioning the "Lock Keys" extension. I was not aware of it and as you stated, it is nicely done.

It looks like most of the gnome-shell extensions  use "gjs" which is the javascript bindings for the Gnome libraries. This piqued my interest because I have programmed Gtk/Gdk in C and also have done "some" javascript programming.

Anyway I came up with the following code that pops up a Gtk window displaying a message that stays on the screen for 5 secs. Notice that it can be styled using css. Just save the code somewhere and make the file executable. Of course the gjs package needs to be installed.

I don't know if this is anything like what you are looking for but hopefully it will be of some use.```
#!/usr/bin/gjs

const Gio = imports.gi.Gio;
const Gtk = imports.gi.Gtk;
const GLib = imports.gi.GLib;

class MessagePopup {
    constructor() {
            this.application = new Gtk.Application({
                application_id: 'org.example.popup',
             });
             this.application.connect('activate', this._onActivate.bind(this));
             this.application.connect('startup', this._onStartup.bind(this));
    }

    _onActivate() {
        this._window.present();
    }

    _onStartup() {
        this._createWidgets();
    }

    _createWidgets() {
        this._window = new Gtk.Window({
            application: this.application,
            window_position: Gtk.WindowPosition.CENTER,
            skip_taskbar_hint: true,   // don't show in taskbar
            default_height: 25,
            default_width: 500
        });
        
        var msg;
     
        if( !ARGV[0] ) {
            msg='Usage: executable "message enclosed in quotes"';
        }
        else {
            msg= ARGV[0];
        }
        
        this.label = new Gtk.Label({
            label: msg 
        });
        
        var css = new Gtk.CssProvider();
        css.load_from_data(" * { font-size: 16px; font-weight: bold; color: white; background-color: black }");
        this.label.get_style_context().add_provider(css, 0);
        this._window.add (this.label);
        this._window.set_decorated(false);   // no title bar
        this._window.show_all();
        GLib.timeout_add( 0, 5000, () => this.application.quit() );  // close after 5 sec.
    }
};

let app = new MessagePopup();
app.application.run (ARGV);



```[https://packages.ubuntu.com/focal/gjs](https://packages.ubuntu.com/focal/gjs)
[https://gitlab.gnome.org/GNOME/gjs/-/blob/master/README.md](https://gitlab.gnome.org/GNOME/gjs/-/blob/master/README.md)

---

### Post by Paddy Landau on 2020-12-14
> **1fallen said:**
> Yup, Gnome adds a new twist to your request…
Thanks for your script, @1fallen, but that still uses notify-send, which is precisely what I'm trying to avoid!
> **norobro said:**
> First, thanks for mentioning the "Lock Keys" extension. I was not aware of it and as you stated, it is nicely done.
Did you notice that you can choose between two different types of notification? OSD goes in the middle of the screen, and Compact looks exactly like the standard Gnome notification. The latter is what I'm really after!
> **norobro said:**
> It looks like most of the gnome-shell extensions  use "gjs"…
It seems that Ubuntu already installs gjs by default, because I already have it.

Thank you for your script. Although it's not quite the same look-and-feel, it does work!

There are two changes that I'd like, if at all possible.

[LIST=1]
[*]I've changed the colours and font to match my theme, but I don't know how to use the CSS to size the message (size 500×70 px) or to position it (the left point (X,Y) should be (737,1)). Do you know how I can do this?
[*]It grabs the focus away from the current window. Is it possible to prevent that, which would make it just like the Gnome notification?
[/LIST]
Thank you again!

---

### Post by norobro on 2020-12-14
You're welcome.

See the comments in red:```
   _createWidgets() {
        this._window = new Gtk.Window({
            application: this.application,
            window_position: Gtk.WindowPosition.CENTER,
            skip_taskbar_hint: true,   // don't show in taskbar
            default_height: 25,          [COLOR=#ff0000]// change to 70[/COLOR]
            accept_focus: false,       [COLOR=#ff0000]// added so window doesn't grab focus[/COLOR]
            default_width: 500
        });
        this._window.move( 737, 1);  [COLOR=#ff0000]// added to relocate window before it is displayed[/COLOR]
        var msg;
        ...
```I don't think you can modify the height/width of a Gtk widget using css. 

We should be able to detect the screen size so the popup will be centered on different sized screens. I'll look into it and post back if I figure it out.

Gnome shell provides a lot of javascript extensions that can be imported. Many are used in extensions like 'Lock Keys', but I'm not familiar enough with gjs to use them. For example here is a link to modules for user interface: [https://gitlab.gnome.org/GNOME/gnome-shell/-/tree/master/js/ui](https://gitlab.gnome.org/GNOME/gnome-shell/-/tree/master/js/ui)

---

### Post by Paddy Landau on 2020-12-15
@norobro, thank you! That works well.

I also removed this line, as I realised that it was redundant:
```
            window_position: Gtk.WindowPosition.CENTER,
```

Do you know if it's possible to prevent the window from grabbing focus?

---

### Post by norobro on 2020-12-15
> **Paddy Landau said:**
> I also removed this line, as I realised that it was redundant:
```
            window_position: Gtk.WindowPosition.CENTER,
```Right you are. Missed that.

So adding "[COLOR=#000000][FONT=&amp]accept_focus: false" doesn't work? I tested it with the at command and the message pops up but doesn't grab focus.[/FONT][/COLOR]```
echo "export DISPLAY=:0;/path/to/executable.js" | at now
```

---

### Post by Paddy Landau on 2020-12-15
> **norobro said:**
> So adding "[COLOR=#000000][FONT=&amp]accept_focus: false" doesn't work?[/FONT][/COLOR]
My bad! Somehow, I missed that line. Yes, it does work, thank you!

I am curious as to why you use "at" to execute the command? I named the script notify-send-transient, so the following works just fine.
```
notify-send-transient 'My message' &
```

---

### Post by norobro on 2020-12-15
> **Paddy Landau said:**
> I am curious as to why you use "at" to execute the command? I named the script notify-send-transient, so the following works just fine.I have been fooling around with at and cron, so I just plugged the script name into a previous command. It is much simpler to background the job, as you did, it just didn't occur to me.

---

### Post by coffeecat on 2022-05-10
Thread re-opened at request of OP.

---

### Post by Paddy Landau on 2022-05-11
> **coffeecat said:**
> Thread re-opened at request of OP.
Thank you!

---

### Post by Paddy Landau on 2022-05-11
On Ubuntu 20.04, the [FONT=&amp]gfs[/FONT] script [FONT=courier new]notify-send-transient[/FONT] has been working perfectly!

Unfortunately, on Ubuntu 22.04 using Gnome 42, it returns an error:
```
Gjs-Message: 07:20:17.035: JS WARNING: [/home/angus/bin/notify-send-transient 9]: Requiring Gtk but it has 2 versions available; use imports.gi.versions to pick one

(gjs:5872): Gjs-CRITICAL **: 07:20:20.434: JS ERROR: Error: No property skip_taskbar_hint on GtkWindow
_init/Gtk.Widget.prototype._init@resource:///org/gnome/gjs/modules/core/overrides/Gtk.js:55:50
_createWidgets@/home/angus/bin/notify-send-transient:30:18
_onStartup@/home/angus/bin/notify-send-transient:26:8
@/home/angus/bin/notify-send-transient:65:17




(gjs:5872): Gjs-CRITICAL **: 07:20:20.435: JS ERROR: TypeError: this._window is undefined
_onActivate@/home/angus/bin/notify-send-transient:22:3
@/home/angus/bin/notify-send-transient:65:17
```
I don't know [FONT=courier new]gfs[/FONT] at all, so I have no idea how to solve this.

Is it a simple fix?

---

### Post by norobro on 2022-05-15
Hi Paddy,

Sorry for taking so long to respond. This is the first time I have logged on in a week or so.  

Try, as the error message says, selecting a Gtk version by adding the line in red:```
#!/usr/bin/gjs
[COLOR=#ff0000]imports.gi.versions.Gtk = "3.0";[/COLOR]
. . .
```

I don't get the error because I am still running 21.04 so I can't test this. I think that the second error is caused by the first.

HTH

---

### Post by Paddy Landau on 2022-05-15
> **norobro said:**
> … selecting a Gtk version by adding the line in red…
That works perfectly, thank you!

---

