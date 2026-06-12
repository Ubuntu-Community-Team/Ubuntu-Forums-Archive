---
title: "Vino no longer working after 22.04 LTS upgrade"
date: 2022-12-03
forum: General Help
---

### Post by uacnt83982803 on 2022-12-03
I have 2 Ubuntu laptops, and connect from one (via Remmina) into the other one (running Vino VNC server).

After the 22.04 upgrade, I can't connect remotely.

On the one that I connect remotely to, I had to re-enable screen sharing.  It's set up with:
```

Remote desktop on
Legacy VNC protocol disabled (off)
Remote control enable on

```

My original remote configuration (connecting using the target computer's IP number) won't work.  It is a static IP and that is the IP that the computer has, and I can ping the target PC from the main pc without any issues.

I added a configuration using the "How to connect" information on the target laptop, "ms-rd://servername.local".  That doesn't give a connection error, but instead shows
```

format.bigEndian =0

``` 
just above where the screen display would be, but I get no response.

Not sure what to do here.

[B]Update:

[/B]I did some more testing.  If I enable the legacy VNC protocol, and select "New connections must ask for access", then when I try to connect I do get the popup on the target PC asking me to either Reject or Approve.  

However, once I select Approve, the screen freezes solid on the target PC, and nothing I can do on it (Ctl Alt Del, System key, Alt-tab, nothing) allows me, on that PC, to do anything.  The only way to recover is via a hard power reset.  Also nothing I can do on the other PC (that I'm connecting from) seems to do anything.  The entire display area (where the remote PC's desktop should appear) is black, and the cursor is a small x.  I tried various things on that PC to try and move the cursor around on the target PC, etc. but nothing.  Also, the name of the remote connection shows up on the Remmina application's title bar, just as it would normally with a functioning connection.

Here's the log from Remmina:
```
(DEBUG) - (rcw_map_event) - Mapping: RemminaConnectionWindow
(DEBUG) - (remmina_protocol_widget_map_event) - Map plugin function not implemented
(DEBUG) - (remmina_protocol_widget_open_connection_real) - Opening connection
(DEBUG) - (remmina_plugin_vnc_init) - Disable smooth scrolling is set to 0
(DEBUG) - (remmina_plugin_vnc_init) - Adding GDK_SMOOTH_SCROLL_MASK
(DEBUG) - (remmina_protocol_widget_open_connection_real) - Have SSH
(DEBUG) - (remmina_protocol_widget_start_direct_tunnel) - SSH tunnel initialization&#8230;
(DEBUG) - (remmina_plugin_vnc_open_connection) - [2022-12-03T17:51:26-05] - me-Aspire-E5-576 - me - Connected to 192.168.1.250:5900 via VNC
(DEBUG) - (remmina_protocol_widget_start_direct_tunnel) - Calling remmina_public_get_server_port
(DEBUG) - (remmina_protocol_widget_start_direct_tunnel) - Calling remmina_public_get_server_port (tunnel)
(DEBUG) - (remmina_protocol_widget_start_direct_tunnel) - server: 192.168.1.250, port: 5900
(DEBUG) - (remmina_plugin_vnc_main) - Color depth: 32
(DEBUG) - (remmina_plugin_vnc_update_quality) - Quality: 2
(DEBUG) - (remmina_plugin_vnc_update_quality) - Encodings: tight zrle ultra copyrect hextile zlib corre rre raw
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: colordepth          = 32
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: format.depth        = 24
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: format.bitsPerPixel = 32
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: format.blueShift    = 0
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: format.redShift     = 16
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: format.trueColour   = 1
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: format.greenShift   = 8
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: format.blueMax      = 255
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: format.redMax       = 255
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: format.greenMax     = 255
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: format.bigEndian    = 0
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: VNC server supports protocol version 3.8 (viewer 3.8)
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: We have 1 security types to read
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: 0) Received security type 1
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: Selecting security type 1 (0/1 in the list)
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: Selected Security Scheme 1
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: No authentication needed
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: VNC authentication succeeded
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: Desktop name "GNOME"
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: Connected to VNC server, using protocol version 3.8
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: VNC server default format:
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned:   32 bits per pixel.
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned:   Least significant byte first in each pixel.
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned:   TRUE colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
(DEBUG) - (remmina_plugin_vnc_main) - Client initialization successfull
(DEBUG) - (remmina_plugin_vnc_main) - Client connected
(DEBUG) - (rco_on_connect) - Connect signal emitted
(DEBUG) - (rco_on_connect) - We save the last successful connection date
(DEBUG) - (remmina_file_state_last_success) - State file /home/me/.cache/remmina/group_vnc_myserver_192-168-1-250.remmina.state.
(DEBUG) - (remmina_file_state_last_success) - Last connection made on 20221203.
(DEBUG) - (rco_on_connect) - Saving credentials
(DEBUG) - (remmina_file_save) - Saving profile
(DEBUG) - (remmina_file_save) - We have a secret and disablepasswordstoring=0
(DEBUG) - (remmina_plugin_glibsecret_delete_password) - password &#8220;password&#8221; deleted for file /home/me/.local/share/remmina/group_vnc_myserver_192-168-1-250.remmina
(DEBUG) - (remmina_file_save) - We have a secret and disablepasswordstoring=0
(DEBUG) - (remmina_plugin_glibsecret_delete_password) - password &#8220;ssh_tunnel_password&#8221; deleted for file /home/me/.local/share/remmina/group_vnc_myserver_192-168-1-250.remmina
(DEBUG) - (remmina_file_save) - We have a secret and disablepasswordstoring=0
(DEBUG) - (remmina_plugin_glibsecret_delete_password) - password &#8220;ssh_tunnel_passphrase&#8221; deleted for file /home/me/.local/share/remmina/group_vnc_myserver_192-168-1-250.remmina
(DEBUG) - (remmina_file_save) - Profile saved
(DEBUG) - (remmina_file_save) - Connection profile states saved
(DEBUG) - (remmina_network_monitor_status) - G_NETWORK_CONNECTIVITY_FULL
(DEBUG) - (rco_on_connect) - Trying to present the window
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: Got new framebuffer size: 1366x768
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: client2server supported messages (bit flags)
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: 00: 00ff 0081 0000 0000 - 0000 0000 0000 0000
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: 08: 0000 0000 0000 0000 - 0000 0000 0000 0000
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: 10: 0000 0000 0000 0000 - 0000 0000 0000 0000
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: 18: 0000 0000 0000 0000 - 0000 0000 0000 0008
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: server2client supported messages (bit flags)
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: 00: 001f 0080 0000 0000 - 0000 0000 0000 0000
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: 08: 0000 0000 0000 0000 - 0000 0000 0000 0000
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: 10: 0000 0000 0000 0000 - 0000 0000 0000 0000
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: 18: 0000 0000 0000 0000 - 0000 0000 0000 0000
(DEBUG) - (remmina_plugin_vnc_rfb_output) - VNC returned: Connected to Server "GNOME Remote Desktop (VNC) (LibVNCServer 0.9.13)"



```

---

### Post by TheFu on 2022-12-03
Intel and the entire x86 line of CPUs use little-endian byte ordering.
Some Motorola and powerPC CPUs use big-endian byte ordering. These are incompatible and if VNC doesn't handle the byte order switching correctly, it won't work.

  I don't know that is the issue, but the message about using big-endian leads me to check that out as the first consideration.

If the systems are on the same subnet, you can use the built-in X/11 capabilities with 'ssh -X' to run GUi programs (not full desktops) on remote systems.  I do this all the time, constantly, right now.  Both my browser and fat email client are working this way now, along with about 10 terminals that are connected into other systems.
On the same LAN, VNC isn't needs and just a waste of bandwidth, IMHO.

My web searches for "VNC endian" didn't return any useful information, so I don't know if VNC handles the issue or not.  I'm 100% positive that X11 does, since I've used X11 in very mixed environments over the decades.

---

### Post by uacnt83982803 on 2022-12-03
I understand what you're saying, but I guess I'd be surprised if VNC changed something between 20.04LTS and 22.04LTS.  Both the local and the remote (target) pc were 20.04LTS until earlier today when I did the upgrade on the target pc to 22.04LTS.

---

### Post by TheFu on 2022-12-03
> **uacnt83982803 said:**
> I understand what you're saying, but I guess I'd be surprised if VNC changed something between 20.04LTS and 22.04LTS.  Both the local and the remote (target) pc were 20.04LTS until earlier today when I did the upgrade on the target pc to 22.04LTS.

Well, things change all the time. I've not been asked if I approved 99.9999999% of the time. Are you?

Are any of the computers non-x86?

Have you tried X11 forwarding through ssh?  I bet that will "just work".

---

### Post by uacnt83982803 on 2022-12-03
I haven't.  I am really trying to avoid having to use that system's desktop physically, since it's stuck up out of sight and until now I've been able to manage it remotely.

---

### Post by TheFu on 2022-12-03
> **uacnt83982803 said:**
> I haven't.  I am really trying to avoid having to use that system's desktop physically, since it's stuck up out of sight and until now I've been able to manage it remotely.

Seems you don't understand. Remote X11 is how to run a program on a remote system, but have the GUI displayed on your local computer.  No special desktop needs to be installed on the remote system.

Try doing this from your normal workstation:
```
$ xterm -geometry 80x25-5+78  -e ssh -X username@remote-server-name.local &
```

Replace "username" with your userid on the remote system.
Replace "remote-server-name.local" with the remote hostname and .local appended if it is any desktop Ubuntu flavor installed, or the IP address if not.
It should be obvious that ssh needs to be running on both systems for this to work.  So, run 
```
sudo apt install ssh fail2ban
``` on both systems if it isn't already working.  I can't imagine having a Linux computer without ssh installed (both the client and server). That would be fairly useless, IMHO.  Installing fail2ban with ssh is a good way to prevent any brute force attacks. If there aren't any, nothing happens. If there are, it will only allow a few from each IP before adding a temporary firewall rule to block more attempts for a few hours. This can be configured, but the defaults are reasonable.  On a secured LAN, it provides just a little protection.

If you aren't familiar with ssh, there are lots of ways to make it more secure AND more convenient. Plus with ssh installed, you get scp, sftp, and the ability for sshfs, rsync, and 50 other tools to use ssh-based key authentication and tunnels automatically.  ssh is considered secure enough for use with hostile govts and over the internet.  How often is something both more secure AND more convenient?  The only thing I know where that is true is ssh. I've never come up with any other tool that provide both.

Oh, and if you don't have an xterm program loaded, you can either install it on the local system OR use a different terminal program. It is completely up to you. There must be 20 popular terminal programs, though I don't know the specific equivalent options for anything except the xterm command shown above. Sorry.  I've been using xterms since the mid-1990s and never bothered with other terminal programs. I'm not a fan of bloat.

---

### Post by uacnt83982803 on 2022-12-03
Solved! 
```

sudo vi /etc/gdm3/custom.conf

```
change this line:

```

# Uncomment the line below to force the login screen to use Xorg
#WaylandEnable=false

```

Lucked across this when doing some searching.  Apparently with Wayland enabled, VNC can only connect to one portion of the window at one time (or something like that).

This seems to have fixed it.

---

### Post by TheFu on 2022-12-03
X11 forwarding is extremely useful and worth having in your tools. Hope you will get it working. The remote windows fully integrate into your local desktop, even while the code behind them runs remotely.  X/Windows has worked this way for about 4 decades, but when ssh added the X/Windows tunnel capability, it drastically changed everything for the better.

Plus, X11 forwarding should work regardless of Wayland or X11 as the display manager.

---

