---
title: "Allowing Non Admin. User Partial Access To Non Root Command"
date: 2021-01-25
forum: General Help
---

### Post by aw1182 on 2021-01-25
I was wondering if someone can help with a problem I'm having.  I created a separate user profile in Ubuntu 20.10 and I want to allow this user to connect to a vpn.  GUI won't allow this because a window pops up asking for admin. password.  I was thinking I could allow partial root access by editing /etc/sudoers.  I added line - standard ALL=(ALL) NOPASSWD: /bin/protonvpn-cli to the file and saved it.  So this basically gives access to all non admin. users access to protonvpn-cli commands.  When I run sudo protonvpn in the terminal I get a message that running protonvpn as root is not supported and is highly discouraged, as it might introduce undesirable side effects.  And then I am asked do I want to proceed.  I hit Y and it works for all the protonvpn commands except protonvpn connect which connects to the vpn servers.  When I run sudo protonvpn connect I get the error: Unknown keyring error occured: Environment variable DBUS_SESSION_BUS_ADDRESS is unset.

So basically is there a way to give access to a specific command to a non admin. user not using root (sudo)?  If not does anyone know how to fix the error that I get when I run sudo protonvpn connect?  Either of these should solve my issue and I would be grateful.

---

### Post by The Cog on 2021-01-25
You don't have to sudo everything as root : you can use sudo to do things as other users.
If you have a user (e.g. vpnuser) that can start the vpn, perhaps
```
sudo -iu vpnuser protonvpn-cli
```
would do the trick.

---

### Post by aw1182 on 2021-01-25
Thanks for the reply/suggestion.  I went on the non admin. account and ran sudo -iu vpnusername protonvpn-cli connect and I get the error:

Sorry, user standard is not allowed to execute '/bin/bash -c protonvpn -cli c' as vpnusername on vpnusername-desktop.

I just realized there may be a another way to fix this but I'm new to Ubuntu and don't know all the commands.  When I run protonvpn -cli connect in the non admin. account I get this error:

Adding ProtonVPN connection...
ProtonVPN connection was successfully added to Network Manager.
Connecting to ProtonVPN on US-TX#20 with UDP...
Traceback (most recent call last):
  File "/usr/bin/protonvpn-cli", line 11, in <module>
    load_entry_point('protonvpn-cli==3.2.0', 'console_scripts', 'protonvpn-cli')()
  File "/usr/lib/python3/dist-packages/protonvpn_cli/main.py", line 21, in main
    ProtonVPNCLI()
  File "/usr/lib/python3/dist-packages/protonvpn_cli/cli.py", line 46, in __init__
    getattr(self, args.command)()
  File "/usr/lib/python3/dist-packages/protonvpn_cli/cli.py", line 50, in c
    self.connect()
  File "/usr/lib/python3/dist-packages/protonvpn_cli/cli.py", line 111, in connect
    self.cli_wrapper.connect(args)
  File "/usr/lib/python3/dist-packages/protonvpn_cli/cli_wrapper.py", line 135, in connect
    ProtonVPNStateMonitor(
  File "/usr/lib/python3/dist-packages/protonvpn_cli/vpn_state_monitor.py", line 27, in __init__
    self.vpn_check()
  File "/usr/lib/python3/dist-packages/protonvpn_cli/vpn_state_monitor.py", line 30, in vpn_check
    vpn_interface = self.get_vpn_interface(True)
  File "/usr/lib/python3/dist-packages/protonvpn_nm_lib/services/dbus_get_wrapper.py", line 97, in get_vpn_interface
    all_settings, iface = self.get_all_conn_settings(
  File "/usr/lib/python3/dist-packages/protonvpn_nm_lib/services/dbus_get_wrapper.py", line 205, in get_all_conn_settings
    return (iface.GetSettings(), iface)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 72, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 141, in __call__
    return self._connection.call_blocking(self._named_service,
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.NetworkManager.Settings.PermissionDenied: uid 1001 has no permission to perform this operation

So looking at the last line of the error it says network manager settings permission denied.  Is there a way to allow access to network settings for the non admin. user?  Maybe going that route might be easier.

---

### Post by aw1182 on 2021-01-25
Or how do I allow user standard to execute '/bin/bash -c protonvpn -cli c' as vpnusername (admin. account) on vpnusername (admin. account)-desktop?

---

### Post by The Cog on 2021-01-25
It has me foxed. "sudo -iu vpnusername protonvpn-cli connect" should run the command "protonvpn-cli connect" but running it as user vpnusername. If vpnusername is able to start the VPN but that sudo command is not, then there is something going on that is beyond my understanding. I was guessing the keyring error was because the vpn key is owned by your vpnuser, not as root. Sorry, but I think you need to wait until someone more knowlegable than I am to look at your problem.

---

### Post by aw1182 on 2021-01-25
Thanks for trying though.  At least I learned about sudo -iu function.  I'll remember that for the future.  I'm sure it will come in handy in other situations.  :D

---

### Post by yancek on 2021-01-25
You can give a user root/sudo permission to run a specific script by editing the sudoers file with:  sudo visudo

Enter something like below where "vpnusername is the actual user name and the full path on the system to where the executable file protonvpn-cli resides:

>  vpnusername ALL=(ALL) NOPASSWD: /path-to/protonvpn-cli 

I guess safely ignore the above as I misread the original post.  If I read correctly this time, you seem to be able to run the script as a specific user but not another user or root w/sudo?

---

### Post by aw1182 on 2021-01-25
Yes you are correct.  I can't run sudo protonvpn-cli connect as root but other protonvpn-cli functions such as sudo protonvpn-cli disconnect.  Anyway I was able to connect just using protonvpn-cli connect.  Somehow its working now the issue now is the connect command works and goes through but then its stopped by the ubuntu gui admin. password window saying user does not have permission to access the network settings.  See post #4 in this thread you can see protonvpn-cli connect work and the error message I get from the terminal.  I need to know how to give permission to change network settings for a non admin. user.  I'm sure there has to be a way to do it.

---

