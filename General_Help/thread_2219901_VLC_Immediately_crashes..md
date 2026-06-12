---
title: "VLC Immediately crashes."
date: 2014-04-25
forum: General Help
---

### Post by WinterMadness on 2014-04-25
I was trying to enable VLC remote, and most of the tutorials are using a later version than Ubuntu uses. So in the interfaces I enabled everything, which realistically shouldnt cause a problem because you'd think you can turn everything off incase its not right. But VLC immediately crashes instead.

This is the output from the console.

```
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x24786f8] [dummy] lua interface error: This is the `dummy' VLC Lua interface module.
[0x24786f8] [dummy] lua interface error: Please specify a VLC Lua interface to load with the --lua-intf option.
[0x24786f8] [dummy] lua interface error: VLC Lua interface modules include: `cli' and `http'.
[0x24786f8] [dummy] lua interface error: For example: vlc -I luaintf --lua-intf cli
[0x24786f8] [dummy] lua interface error: You can also use the alternate syntax: vlc -I "luaintf{intf=cli}"
[0x24786f8] [dummy] lua interface error: See share/lua/intf/README.txt for more information about lua interface modules.
[0x2476428] [http] lua interface: Lua HTTP interface
[0x23cc7c8] [telnet] lua interface: Listening on host "telnet://localhost:4212".
[0x2476c68] [cli] lua interface: Listening on host "*console".
VLC media player 2.0.8 Twoflower
Command Line Interface initialized. Type `help' for help.
> Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.
[0x23e9788] fbosd interface error: cannot open /dev/fb0 (Permission denied)
[0x23e9788] main interface error: no suitable interface module

```

if I can just turn everything off except the web interface then it will work again.

---

### Post by WinterMadness on 2014-04-26
I was able to solve this by deleting the config file:

```

rm ~/.config/vlc/vlcrc

```

---

