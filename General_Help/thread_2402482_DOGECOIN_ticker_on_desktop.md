---
title: "DOGECOIN ticker on desktop"
date: 2018-09-30
forum: General Help
---

### Post by shawnhustlerussell2 on 2018-09-30
I can find quite a few websites that generate HTML files to display current crypto-currency prices, I have looked and looked but cannot find a way to translate this into a "desktop widget" for Ubuntu 16.04. I tried Conky, I tried Screenlets, I tried to read some things about making an HTML widget for my desktop, but I cannot seem to get it figured out. Guess I could use some advice here. Thanks guys and gals!

---

### Post by again? on 2018-11-04
You can use nodejs to install coinmon.
Coinmon is a cli cryptocurrency price tool.
[ATTACH=CONFIG]281527[/ATTACH]

You can display in conky by removing the color codes with sed.
[ATTACH=CONFIG]281528[/ATTACH]



I used this guide to install nodejs... [Install The Latest Node.Js And NMP Packages On Ubuntu 16.04 / 18.04 LTS]("https://websiteforstudents.com/install-the-latest-node-js-and-nmp-packages-on-ubuntu-16-04-18-04-lts/")
Then install coinmon.
```
sudo npm install -g coinmon
```
To check the top 10 cryptocurrencies ranked by their market cap, simply enter in terminal...
```
coinmon
```
See coinman command options here--->  [https://github.com/bichenkk/coinmon](https://github.com/bichenkk/coinmon)


This is the conky config I used to display just dogecoin coinmon output in $AUD.
```
conky.config = {
    alignment = 'bottom_right',
    background = false,
    border_width = 1,
    cpu_avg_samples = 2,
    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    use_xft = true,
    font = 'Ubuntu Mono:size=10',
    override_utf8_locale = true,
    gap_x = 5,
    gap_y = 60,
    minimum_height = 5,
    minimum_width = 5,
    net_avg_samples = 2,
    no_buffers = true,
    double_buffer = true,
    out_to_console = false,
    out_to_stderr = false,
    extra_newline = false,
    text_buffer_size = 1024,
    own_window_title = 'Conky',
    own_window = true,
    own_window_transparent = true,
    own_window_type = 'normal',
    own_window_hints = 'undecoratecoinmand,below,sticky,skip_taskbar,skip_pager',
    own_window_argb_visual = false,
--    own_window_argb_value = 0,

    stippled_borders = 0,
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    show_graph_scale = false,
    show_graph_range = false,
    max_user_text = 8000,
    text_buffer_size = 1024,
    imlib_cache_size = 0,
    imlib_cache_flush_interval = 60,
}


conky.text = [[
${execi 60 coinmon -c aud -f doge | sed -r 's/\x1B\[([0-9]{1,2}(;[0-9]{1,2})?)?[mGK]//g'}
]]
```
[ATTACH=CONFIG]281529[/ATTACH]

If you prefer the coloured terminal output, an alternative to conky is to place  an undecorated  terminal on the desktop.
I'm using xfce4-terminal which you can install in other desktops.
Create a loop script.
_coinloop.sh_
```
#!/bin/sh

## sets the xfce4-terminal titled xfcoin to below
wmctrl -a xfcoin -b toggle,below

while [ 1 ]; do
        clear 
	coinmon -c aud -f doge
	sleep 60   #set your update interval in secs
done
exit 0
```
Save and make executable.
Install wmctrl to set the window below.

Then in start up applications put this command (test in terminal) ...
```
xfce4-terminal --hide-borders --hide-menubar --hide-toolbar --hide-scrollbar --title=xfcoin --font="Ubuntu Mono 10" --geometry=86x8-0-33 -e "[COLOR="#FF0000"]/home/glen/scripts/coinloop.sh[/COLOR]"
```
Edit for [COLOR="#FF0000"]your path[/COLOR] to coinloop.sh.

You may need to adjust some of the terminal options for your screen size.
For my 1680x1050 screen it sits in the bottom right corner.

---

