---
title: "Issue with Snap version of Minecraft and AppArmor"
date: 2021-10-19
forum: General Help
---

### Post by couzin2000 on 2021-10-19
Recently got into this game, but for some reason my fresh install of Ubuntu Focal Fossa LTS doesn't play well. 
I downloaded Minecraft Java thru snapd. Installed. The launcher runs fine. When I hit "Play Demo", here's the verbose I get from logs:

```
17:00:04.191
Backend library: LWJGL version 3.2.2 build 10
17:00:06.509
[COLOR="#FF0000"]ERROR:dbus.proxies:Introspect error on :1.69:/org/freedesktop/Notifications: dbus.exceptions.DBusException: 
org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; t
ype="method_call", sender=":1.189" (uid=1000 pid=9389 comm="python3 -c import dbus;bus=dbus.SessionBus();notif" 
label="snap.mc-installer.mc-installer (enforce)") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error 
name="(unset)" requested_reply="0" destination=":1.69" (uid=1000 pid=1692 comm="/usr/bin/gjs /usr/share/gnome-shell/org.gnome.Shel" 
label="unconfined")[/COLOR]
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/snap/mc-installer/570/gnome-platform/usr/lib/python3/dist-packages/dbus/proxies.py", line 72, in __call__
    return self._proxy_method(*args, **keywords)
  File "/snap/mc-installer/570/gnome-platform/usr/lib/python3/dist-packages/dbus/proxies.py", line 141, in __call__
    return self._connection.call_blocking(self._named_service,
  File "/snap/mc-installer/570/gnome-platform/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.InvalidArgs: Type of message, &#8220;(sisssssi)&#8221;, does not match expected type &#8220;(susssasa{sv}i)&#8221;
  <log4j:Event logger="net.minecraft.client.main.Main" timestamp="1634677206508" level="WARN" thread="Render thread">
    <log4j:Message><![CDATA[Failed to create window: ]]></log4j:Message>
    <log4j:Throwable><![CDATA[dpr$a: GLFW error 65543: GLX: Failed to create context: GLXBadFBConfig
	at dpr.b(SourceFile:218)
	at org.lwjgl.glfw.GLFWErrorCallbackI.callback(GLFWErrorCallbackI.java:36)
	at org.lwjgl.system.JNI.invokePPPP(Native Method)
	at org.lwjgl.glfw.GLFW.nglfwCreateWindow(GLFW.java:1714)
	at org.lwjgl.glfw.GLFW.glfwCreateWindow(GLFW.java:1897)
	at dpr.<init>(SourceFile:92)
	at enx.a(SourceFile:21)
	at dvp.<init>(SourceFile:481)
	at net.minecraft.client.main.Main.main(SourceFile:179)
]]></log4j:Throwable>
  </log4j:Event>
17:00:06.509
XML_ERROR_PARSING
17:00:06.703

17:00:06.704
Process ended with exit code 0
```

How can I fix the AppArmor issue preventing me from playing? Serious noob in coding here.

---

### Post by couzin2000 on 2021-10-21
Bump... anyone?

---

### Post by grahammechanical on 2021-10-21
There is something you could try. Open Ubuntu Software and search for Minecraft. You might find a permissions tab that allows you to make some adjustments. Or, you might find that the demo version is even more restricted than the full game would be. Alternatively, ask the developer who produced the snap package of this application. I do not know the license that Minecraft is distributed under but it is possible to snap package an application even if you are not the actual application developer. This could result in snap packaged applications that do not have all the working features of the original application.

Regards

---

### Post by Tadaen_Sylvermane on 2021-10-23
Can I ask why you don't just get the official tar.gz and use the executable inside it? It's a single file, no installation required. I found the .deb to not work well. Fails to connect regularly. 

[https://launcher.mojang.com/download/Minecraft.tar.gz](https://launcher.mojang.com/download/Minecraft.tar.gz)

---

### Post by couzin2000 on 2021-10-25
Yes you may ask. I got the snap after having installed a minimal install of FF LTS. I didnt install anything else, it's a fresh install, and I wanna find out if I can run the game. That said, the .deb and .rpm versions I was having a difficult time installing, and they would not run at all. I was able to purge these versions and install the snap version which looks like it gets further along. But while running the demo, I encounter the AppArmor error, and somehow I am convinced that this would be a small workaround... still, I don't know enough about AppArmor to adjust it in any way.  Hence my post here.

---

