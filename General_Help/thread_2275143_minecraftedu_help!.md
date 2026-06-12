---
title: "minecraftedu help!"
date: 2015-04-24
forum: General Help
---

### Post by cmcanulty on 2015-04-24
all of the sudden none of our library minecraftedu clients will run. In trying to make the launcher.jar file to open with java I may have totally screwed everything up. I have spent hours trying to purge all java and reinstall but nothing works. Kids are going to arrive for game night and not be able to do anything. Apparently java has so many files and associated things that purging it and reinstalling is very difficult. Even on the machines I haven't done anything to the launcher.jar won't open. Before just double clicking it opened minecraftedu. All clients are xubuntu14.04 64bit the server is win 7 pro and server opens fine. I am very frustrated and upset,please someone help soon.

I found this and it may help but I am not sure how to do it and I don't want to lock in a java version in path as then every time java updates I have to redo a fix on 10-12 computers. Here is the java version I am running which may or may not be another issue

```
darcy@ubuntu3:~$  java -version
java version "1.7.0_79"
OpenJDK Runtime Environment (IcedTea 2.5.5) (7u79-2.5.5-0ubuntu0.14.04.2)
OpenJDK 64-Bit Server VM (build 24.79-b02, mixed mode)
darcy@ubuntu3:~$ 

```


```
Setting Path on Solaris and Linux
To find out if the java executable is in your PATH, execute:
% java -version

This will print the version of the java executable, if it can find it. If you get error java: Command not found. Then path is not properly set.

To find out which java executable the first one found in your PATH, execute:
% which java

Below are the steps to set the PATH permanently,
Note: We are here giving instructions for two most popular Shells on Linux and Solaris.
Please visit link below if you are using any other shells.
Path Setting Tutorial

For bash Shell:

    Edit the startup file (~/ .bashrc)
    Modify PATH variable:
    PATH="$PATH":/usr/local/jdk1.6.0/bin
    export PATH
    Save and close the file
    Open new Terminal window
    Verify the PATH is set properly
    % java -version
```

---

### Post by Karlchen on 2015-04-24
Hello, cmcanulty.

As user altair4 reported in a another forum, [openjre not running java apps as executive after last update]("http://forums.linuxmint.com/viewtopic.php?f=47&t=194745#p1010356"), the update to openjdk7u79 removes the launcher file /usr/share/applications/openjdk-7-java.desktop.
It does doso although in the changelog there is an entry which states: "* Only install the openjdk-java.desktop file when using cautious-launcher."
The result, however, is that clicking on an any .jar file inside your file-manager in order to launch it will no longer have the desired effect.

Could it be that you experience the effect of the missing launcher file openjdk-7-java.desktop?

If so, you might re-create it,
+ either with root permissions in the folder /usr/share/applications
+ or under your own account in the folder ~/.local/share/applications

Filename: openjdk-7-java.desktop
Content: ```
[Desktop Entry]
Name=OpenJDK Java 7 Runtime
Comment=OpenJDK Java 7 Runtime
Exec=cautious-launcher %f /usr/bin/java -jar
Terminal=false
Type=Application
Icon=openjdk-7
MimeType=application/x-java-archive;application/java-archive;application/x-jar;
NoDisplay=true
```

Under normal circumstances, i.e. right after the upgrade this should have been sufficient to return normal functionality. Yet, as you have fiddled around manually, you may have broken more than had been broken by the update (unless I have misunderstood your post).

Here the following openjdk7 packages are present: ```
$ dpkg --list openjdk* icedtea* | grep "^ii"
ii  icedtea-7-jre-jamvm                    7u79-2.5.5-0ubuntu0.12.04.1             Alternative JVM for OpenJDK, using JamVM
ii  icedtea-7-plugin                       1.2.3-0ubuntu0.12.04.4                  web browser plugin based on OpenJDK and IcedTea to execute Java applets
ii  icedtea-netx                           1.2.3-0ubuntu0.12.04.4                  NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icedtea-netx-common                    1.2.3-0ubuntu0.12.04.4                  NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  openjdk-7-jre                          7u79-2.5.5-0ubuntu0.12.04.1             OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-7-jre-headless                 7u79-2.5.5-0ubuntu0.12.04.1             OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-7-jre-lib                      7u79-2.5.5-0ubuntu0.12.04.1             OpenJDK Java runtime (architecture independent libraries)
```
As you are using Ubuntu 14.04.2, whereas my list has been taken from Ubuntu 12.04.5, the exact package version strings will be different on your system. But the package names to re-install will be the same.

So more likely than not executing ```
sudo apt-get update
sudo apt-get install openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib icedtea-7-jre-jamvm icedtea-7-plugin icedtea-netx icedtea-netx-common
``` should return Java into a functional state again.
In case you prefer using Synaptic over using the commandline, this will be fine as well.

Do not forget to (re)create the missing launcher file openjdk-7-java.desktop afterwards.

HTH,
Karl

---

### Post by Karlchen on 2015-04-24
[SIZE=1]**<duplicated post above stupidly>**
This is why I emptied this post.
**</duplicated post above stupidly>**[/SIZE]

---

### Post by cmcanulty on 2015-04-24
thanks I will try in am , I am fried from fighting this all day

---

### Post by efflandt on 2015-04-24
I am just curious what minecraftedu is. Is that a group or club of people who play minecraft or a clone of minecraft? And how are you launching the minecraft launcher? I am currently running 64-bit 14.04 and have been using the following .desktop file for some time to launch minecraft. The icon was extracted from a minecraft.jar file a long time ago:```
efflandt@XPS-8100-1404:~/Desktop$ ls -l Minecraft*
-rwxrwxr-x 1 efflandt efflandt 202 Dec 30 21:49 Minecraft.desktop
-rwxrwxr-x 1 efflandt efflandt 276 Dec 30 21:49 Minecraft Server.desktop

efflandt@XPS-8100-1404:~/Desktop$ cat Minecraft.desktop

[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon=/home/efflandt/Pictures/Icons/minecraft.png
Name=Minecraft-direct
Exec=sh -c 'java -jar ~/Downloads/Minecraft.jar'
Name[en_US]=Minecraft

efflandt@XPS-8100-1404:~/Desktop$ dpkg --list openjdk* icedtea* | grep "^ii"
ii  icedtea-7-plugin:amd64                                1.5-1ubuntu1                                           amd64        web browser plugin based on OpenJDK and IcedTea to execute Java applets
ii  icedtea-netx:amd64                                    1.5-1ubuntu1                                           amd64        NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icedtea-netx-common                                   1.5-1ubuntu1                                           all          NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icedtea-plugin                                        1.5-1ubuntu1                                           all          web browser plugin to execute Java applets (dependency package)
ii  openjdk-7-jre:amd64                                   7u79-2.5.5-0ubuntu0.14.04.2                            amd64        OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-7-jre-headless:amd64                          7u79-2.5.5-0ubuntu0.14.04.2                            amd64        OpenJDK Java runtime, using Hotspot JIT (headless)
```

---

### Post by cmcanulty on 2015-04-25
Wow, thanks, I never would have figured that out myself. I also did a tweak that made a desktop shortcut to Launcher.jar work by installing jarwrapper, setting  the shortcut as executable and setting it to open with jarwrapper. I have it installed and working correctly in 9 desktops have one to go that is currently being used. I hope this trauma doesn't hit every time jre updates! I read minecraftedu has plans to make it work without java for win and mac but of course linux is forgotten.Thanks for all your help this only sucked up 3 of my days this week. I don't play computer games so this is only something I do to support our library.

[http://http://www.howtogeek.com/210907/minecraft-doesnt-need-java-installed-anymore-its-time-to-remove-it/]("http://http://www.howtogeek.com/210907/minecraft-doesnt-need-java-installed-anymore-its-time-to-remove-it/")

---

### Post by cmcanulty on 2015-04-27
unfortunately one computer won't run it after the fix. It opens the window where I pick start minecraft edu and then the new box where I click launch then the black game box opens and immediately crashes I don't know what else could be needed on that computer I did reinstall that one last week is there another dependency I could be missing? I have the opejdk 7 and the desktop things fixed already as you suggested. All the machines have identical specs
Maybe this will help it is the client log

```
Debug logging for Minecraft Client started at: 27. April. 2015 18:01
###############################################
MinecraftEdu version: 1.7.10 build 12 Classroom
PATHS:
pathMapQuestionLocationsFile /home/darcy/minecraftedu/minecraft/quizQuestions.ini
pathIgnoredClientMods /home/darcy/minecraftedu/minecraft/../launcher_res/settings/ignoredclientmods.ini
pathOrigOptionsFile /home/darcy/minecraftedu/minecraft/../launcher_res/settings/options_orig.txt
pathServerTexturesFile /home/darcy/minecraftedu/minecraft/resourcepacks/eduserverresourcepack.zip
pathOptionsFile /home/darcy/minecraftedu/minecraft/options.txt
pathEduSettingsFile /home/darcy/minecraftedu/minecraft/minecraftedusettings.ini
pathEduKeybindings /home/darcy/minecraftedu/minecraft/../launcher_res/settings/edukeybindings.ini
pathExternalLibraries ./lib/
pathDebugWritingFile /home/darcy/minecraftedu/minecraft/../debug/client.log
pathLauncherSettingsFile /home/darcy/minecraftedu/minecraft/../launcher_res/settings/launchersettings.ini
###############################################
Completely ignored arguments: [${user_properties}, ]
If on Windows, make sure to provide all of the necessary dll's as specified in the twitchsdk README. Also, make sure to set the PATH environment variable to point to the directory containing the dll's.

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.
---- Minecraft Crash Report ----
// But it works on my machine.

Time: 4/27/15 6:01 PM
Description: Registering texture

org.lwjgl.LWJGLException: X Error - disp: 0x7f4b74ad8800 serial: 148 error: GLXBadRenderRequest request_code: 148 minor_code: 1
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:321)
	at org.lwjgl.opengl.GL11.nglGenTextures(Native Method)
	at org.lwjgl.opengl.GL11.glGenTextures(GL11.java:1407)
	at net.minecraft.client.renderer.texture.TextureUtil.func_110996_a(SourceFile:57)
	at net.minecraft.client.renderer.texture.AbstractTexture.func_110552_b(SourceFile:9)
	at net.minecraft.client.renderer.texture.SimpleTexture.func_110551_a(SourceFile:48)
	at net.minecraft.client.renderer.texture.TextureManager.func_110579_a(SourceFile:72)
	at net.minecraft.client.renderer.texture.TextureManager.func_110577_a(SourceFile:40)
	at net.minecraft.client.gui.FontRenderer.<init>(FontRenderer.java:73)
	at net.minecraft.client.Minecraft.func_71384_a(Minecraft.java:488)
	at net.minecraft.client.Minecraft.func_99999_d(Minecraft.java:872)
	at net.minecraft.client.main.Main.main(Main.java:186)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at net.minecraft.launchwrapper.Launch.launch(Launch.java:134)
	at net.minecraft.launchwrapper.Launch.main(Launch.java:28)


A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------

-- Head --
Stacktrace:
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:321)
	at org.lwjgl.opengl.GL11.nglGenTextures(Native Method)
	at org.lwjgl.opengl.GL11.glGenTextures(GL11.java:1407)
	at net.minecraft.client.renderer.texture.TextureUtil.func_110996_a(SourceFile:57)
	at net.minecraft.client.renderer.texture.AbstractTexture.func_110552_b(SourceFile:9)
	at net.minecraft.client.renderer.texture.SimpleTexture.func_110551_a(SourceFile:48)

-- Resource location being registered --
Details:
	Resource location: minecraft:textures/font/ascii.png
	Texture object class: net.minecraft.client.renderer.texture.SimpleTexture
Stacktrace:
	at net.minecraft.client.renderer.texture.TextureManager.func_110579_a(SourceFile:72)
	at net.minecraft.client.renderer.texture.TextureManager.func_110577_a(SourceFile:40)
	at net.minecraft.client.gui.FontRenderer.<init>(FontRenderer.java:73)
	at net.minecraft.client.Minecraft.func_71384_a(Minecraft.java:488)

-- Initialization --
Details:
Stacktrace:
	at net.minecraft.client.Minecraft.func_99999_d(Minecraft.java:872)
	at net.minecraft.client.main.Main.main(Main.java:186)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at net.minecraft.launchwrapper.Launch.launch(Launch.java:134)
	at net.minecraft.launchwrapper.Launch.main(Launch.java:28)

-- System Details --
Details:
	Minecraft Version: 1.7.10
	Operating System: Linux (amd64) version 3.13.0-49-generic
	Java Version: 1.7.0_79, Oracle Corporation
	Java VM Version: OpenJDK 64-Bit Server VM (mixed mode), Oracle Corporation
	Memory: 178826040 bytes (170 MB) / 267911168 bytes (255 MB) up to 652738560 bytes (622 MB)
	JVM Flags: 1 total; -Xmx700m
	AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
	IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
	FML: MCP v9.03 FML v7.10.25.0 Minecraft Forge 10.13.0.1208 4 mods loaded, 4 mods active
	mcp{9.05} [Minecraft Coder Pack] (minecraft.jar) Unloaded->Constructed->Pre-initialized
	FML{7.10.25.0} [Forge Mod Loader] (mceduforge-0.jar) Unloaded->Constructed->Pre-initialized
	Forge{10.13.0.1208} [Minecraft Forge] (mceduforge-0.jar) Unloaded->Constructed->Pre-initialized
	mcedu{1.7.10} [MinecraftEdu] (mceduforge-0.jar) Unloaded->Constructed->Pre-initialized
	Launched Version: mceduforge
	LWJGL: 2.9.1
	OpenGL: Mesa GLX Indirect GL version 1.3 Mesa 4.0.4, Mesa project: www.mesa3d.org
	GL Caps: Using GL 1.3 multitexturing.
Not using framebuffer objects because OpenGL 1.4 is not supported, EXT_blend_func_separate is not supported, OpenGL 3.0 is not supported, ARB_framebuffer_object is not supported, and EXT_framebuffer_object is not supported.
Anisotropic filtering is not supported.
Shaders are not available because OpenGL 2.1 is not supported, ARB_shader_objects is not supported, ARB_vertex_shader is not supported, and ARB_fragment_shader is not supported.

	Is Modded: Definitely; Client brand changed to 'fml,forge'
	Type: Client (map_client.txt)
	Resource Packs: [mcedu_resourcepack.zip]
	Current Language: English (US)
	Profiler Position: N/A (disabled)
	Vec3 Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
	Anisotropic Filtering: Off (1)

#@!@# Game crashed! Crash report saved to: #@!@# /home/darcy/minecraftedu/minecraft/crash-reports/crash-2015-04-27_18.01.31-client.tx
```t

and here is the launcher log
```
Debug logging for MinecraftEdu Launcher started at: 27. April. 2015 18:00
###############################################
MinecraftEdu version: 1.7.10 build 12 Classroom
PATHS:
###############################################
Launcher 1.2.1 (through bootstrap 4) started on linux...
Current time is Apr 27, 2015 6:01:04 PM
System.getProperty('os.name') == 'Linux'
System.getProperty('os.version') == '3.13.0-49-generic'
System.getProperty('os.arch') == 'amd64'
System.getProperty('java.version') == '1.7.0_79'
System.getProperty('java.vendor') == 'Oracle Corporation'
System.getProperty('sun.arch.data.model') == '64'
Loaded 2 profile(s); selected 'MinecraftEdu'
Loaded 2 profile(s); selected 'MinecraftEdu'
mceduforge
Looking for old natives to clean up...
Unpacking natives to /home/darcy/minecraftedu/minecraft/versions/mceduforge/mceduforge-natives-102546894157
Launching in /home/darcy/minecraftedu/minecraft
Running /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java -Xmx700m -Dfml.ignoreInvalidMinecraftCertificates=true -Djava.library.path=/home/darcy/minecraftedu/minecraft/versions/mceduforge/mceduforge-natives-102546894157 -cp /home/darcy/minecraftedu/minecraft/libraries/minecraftedu/mceduforge/0/mceduforge-0.jar:/home/darcy/minecraftedu/minecraft/libraries/com/sk89q/worldedit/5.5.6/worldedit-5.5.6.jar:/home/darcy/minecraftedu/minecraft/libraries/net/minecraft/launchwrapper/1.9/launchwrapper-1.9.jar:/home/darcy/minecraftedu/minecraft/libraries/org/ow2/asm/asm-all/4.1/asm-all-4.1.jar:/home/darcy/minecraftedu/minecraft/libraries/org/scala-lang/scala-library/2.10.2/scala-library-2.10.2.jar:/home/darcy/minecraftedu/minecraft/libraries/org/scala-lang/scala-compiler/2.10.2/scala-compiler-2.10.2.jar:/home/darcy/minecraftedu/minecraft/libraries/net/sf/jopt-simple/jopt-simple/4.5/jopt-simple-4.5.jar:/home/darcy/minecraftedu/minecraft/libraries/lzma/lzma/0.0.1/lzma-0.0.1.jar:/home/darcy/minecraftedu/minecraft/libraries/com/mojang/realms/1.2.4/realms-1.2.4.jar:/home/darcy/minecraftedu/minecraft/libraries/org/apache/commons/commons-compress/1.8.1/commons-compress-1.8.1.jar:/home/darcy/minecraftedu/minecraft/libraries/org/apache/httpcomponents/httpclient/4.3.3/httpclient-4.3.3.jar:/home/darcy/minecraftedu/minecraft/libraries/commons-logging/commons-logging/1.1.3/commons-logging-1.1.3.jar:/home/darcy/minecraftedu/minecraft/libraries/org/apache/httpcomponents/httpcore/4.3.2/httpcore-4.3.2.jar:/home/darcy/minecraftedu/minecraft/libraries/java3d/vecmath/1.3.1/vecmath-1.3.1.jar:/home/darcy/minecraftedu/minecraft/libraries/net/sf/trove4j/trove4j/3.0.3/trove4j-3.0.3.jar:/home/darcy/minecraftedu/minecraft/libraries/com/ibm/icu/icu4j-core-mojang/51.2/icu4j-core-mojang-51.2.jar:/home/darcy/minecraftedu/minecraft/libraries/com/paulscode/codecjorbis/20101023/codecjorbis-20101023.jar:/home/darcy/minecraftedu/minecraft/libraries/com/paulscode/codecwav/20101023/codecwav-20101023.jar:/home/darcy/minecraftedu/minecraft/libraries/com/paulscode/libraryjavasound/20101123/libraryjavasound-20101123.jar:/home/darcy/minecraftedu/minecraft/libraries/com/paulscode/librarylwjglopenal/20100824/librarylwjglopenal-20100824.jar:/home/darcy/minecraftedu/minecraft/libraries/com/paulscode/soundsystem/20120107/soundsystem-20120107.jar:/home/darcy/minecraftedu/minecraft/libraries/io/netty/netty-all/4.0.10.Final/netty-all-4.0.10.Final.jar:/home/darcy/minecraftedu/minecraft/libraries/com/google/guava/guava/16.0/guava-16.0.jar:/home/darcy/minecraftedu/minecraft/libraries/org/apache/commons/commons-lang3/3.2.1/commons-lang3-3.2.1.jar:/home/darcy/minecraftedu/minecraft/libraries/commons-io/commons-io/2.4/commons-io-2.4.jar:/home/darcy/minecraftedu/minecraft/libraries/commons-codec/commons-codec/1.9/commons-codec-1.9.jar:/home/darcy/minecraftedu/minecraft/libraries/net/java/jinput/jinput/2.0.5/jinput-2.0.5.jar:/home/darcy/minecraftedu/minecraft/libraries/net/java/jutils/jutils/1.0.0/jutils-1.0.0.jar:/home/darcy/minecraftedu/minecraft/libraries/com/google/code/gson/gson/2.2.4/gson-2.2.4.jar:/home/darcy/minecraftedu/minecraft/libraries/com/mojang/authlib/1.5.13/authlib-1.5.13.jar:/home/darcy/minecraftedu/minecraft/libraries/org/apache/logging/log4j/log4j-api/2.0-beta9/log4j-api-2.0-beta9.jar:/home/darcy/minecraftedu/minecraft/libraries/org/apache/logging/log4j/log4j-core/2.0-beta9/log4j-core-2.0-beta9.jar:/home/darcy/minecraftedu/minecraft/libraries/org/lwjgl/lwjgl/lwjgl/2.9.1/lwjgl-2.9.1.jar:/home/darcy/minecraftedu/minecraft/libraries/org/lwjgl/lwjgl/lwjgl_util/2.9.1/lwjgl_util-2.9.1.jar:/home/darcy/minecraftedu/minecraft/libraries/tv/twitch/twitch/5.16/twitch-5.16.jar:/home/darcy/minecraftedu/minecraft/versions/mceduforge/mceduforge.jar net.minecraft.launchwrapper.Launch --username Player16424 --version mceduforge --gameDir /home/darcy/minecraftedu/minecraft --assetsDir /home/darcy/minecraftedu/minecraft/assets --assetIndex 1.7.10 --uuid 00000000-0000-0000-0000-000000000000 --accessToken ${auth_access_token} --userProperties ${user_properties} --userType ${user_type} --userProperties {} --tweakClass cpw.mods.fml.common.launcher.FMLTweaker 
Client> [18:01:12] [main/INFO] [LaunchWrapper]: Loading tweak class name cpw.mods.fml.common.launcher.FMLTweaker
Client> [18:01:12] [main/INFO] [LaunchWrapper]: Using primary tweak class name cpw.mods.fml.common.launcher.FMLTweaker
Client> [18:01:12] [main/INFO] [LaunchWrapper]: Calling tweak class cpw.mods.fml.common.launcher.FMLTweaker
Client> [18:01:12] [main/INFO] [FML]: Forge Mod Loader version 7.10.25.0 for Minecraft 1.7.10 loading
Client> [18:01:12] [main/INFO] [FML]: Java is OpenJDK 64-Bit Server VM, version 1.7.0_79, running on Linux:amd64:3.13.0-49-generic, installed at /usr/lib/jvm/java-7-openjdk-amd64/jre
Client> [18:01:12] [main/INFO] [LaunchWrapper]: Loading tweak class name cpw.mods.fml.common.launcher.FMLInjectionAndSortingTweaker
Client> [18:01:12] [main/INFO] [LaunchWrapper]: Loading tweak class name cpw.mods.fml.common.launcher.FMLDeobfTweaker
Client> [18:01:12] [main/INFO] [LaunchWrapper]: Calling tweak class cpw.mods.fml.common.launcher.FMLInjectionAndSortingTweaker
Client> [18:01:12] [main/INFO] [LaunchWrapper]: Calling tweak class cpw.mods.fml.common.launcher.FMLInjectionAndSortingTweaker
Client> [18:01:12] [main/INFO] [LaunchWrapper]: Calling tweak class cpw.mods.fml.relauncher.CoreModManager$FMLPluginWrapper
Client> [18:01:16] [main/INFO] [FML]: Found valid fingerprint for Minecraft. Certificate fingerprint cd99959656f753dc28d863b46769f7f8fbaefcfc
Client> [18:01:16] [main/ERROR] [FML]: FML appears to be missing any signature data. This is not a good thing
Client> [18:01:16] [main/INFO] [LaunchWrapper]: Calling tweak class cpw.mods.fml.relauncher.CoreModManager$FMLPluginWrapper
Client> [18:01:16] [main/INFO] [LaunchWrapper]: Calling tweak class cpw.mods.fml.common.launcher.FMLDeobfTweaker
Client> [18:01:17] [main/INFO] [LaunchWrapper]: Loading tweak class name cpw.mods.fml.common.launcher.TerminalTweaker
Client> [18:01:17] [main/INFO] [LaunchWrapper]: Calling tweak class cpw.mods.fml.common.launcher.TerminalTweaker
Client> [18:01:17] [main/INFO] [LaunchWrapper]: Launching wrapped minecraft {net.minecraft.client.main.Main}
Client> Debug logging for Minecraft Client started at: 27. April. 2015 18:01
Client> ###############################################
Client> MinecraftEdu version: 1.7.10 build 12 Classroom
Client> PATHS:
Client> pathMapQuestionLocationsFile /home/darcy/minecraftedu/minecraft/quizQuestions.ini
Client> pathIgnoredClientMods /home/darcy/minecraftedu/minecraft/../launcher_res/settings/ignoredclientmods.ini
Client> pathOrigOptionsFile /home/darcy/minecraftedu/minecraft/../launcher_res/settings/options_orig.txt
Client> pathServerTexturesFile /home/darcy/minecraftedu/minecraft/resourcepacks/eduserverresourcepack.zip
Client> pathOptionsFile /home/darcy/minecraftedu/minecraft/options.txt
Client> pathEduSettingsFile /home/darcy/minecraftedu/minecraft/minecraftedusettings.ini
Client> pathEduKeybindings /home/darcy/minecraftedu/minecraft/../launcher_res/settings/edukeybindings.ini
Client> pathExternalLibraries ./lib/
Client> pathDebugWritingFile /home/darcy/minecraftedu/minecraft/../debug/client.log
Client> pathLauncherSettingsFile /home/darcy/minecraftedu/minecraft/../launcher_res/settings/launchersettings.ini
Client> ###############################################
Client> [18:01:21] [main/INFO]: Setting user: Player16424
Client> Completely ignored arguments: [${user_properties}, ]
Client> [18:01:23] [Client thread/INFO]: LWJGL Version: 2.9.1
Client> libGL error: failed to load driver: swrast
Client> [18:01:24] [Client thread/ERROR]: Couldn't set pixel format
Client> org.lwjgl.LWJGLException: Could not choose visual
Client> 	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method) ~[lwjgl-2.9.1.jar:?]
Client> 	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61) ~[lwjgl-2.9.1.jar:?]
Client> 	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:818) ~[lwjgl-2.9.1.jar:?]
Client> 	at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61) ~[lwjgl-2.9.1.jar:?]
Client> 	at org.lwjgl.opengl.Display.create(Display.java:846) ~[lwjgl-2.9.1.jar:?]
Client> 	at org.lwjgl.opengl.Display.create(Display.java:757) ~[lwjgl-2.9.1.jar:?]
Client> 	at net.minecraftforge.client.ForgeHooksClient.createDisplay(ForgeHooksClient.java:327) ~[ForgeHooksClient.class:1.7.2]
Client> 	at net.minecraft.client.Minecraft.func_71384_a(Minecraft.java:432) [bao.class:?]
Client> 	at net.minecraft.client.Minecraft.func_99999_d(Minecraft.java:872) [bao.class:?]
Client> 	at net.minecraft.client.main.Main.main(Main.java:186) [Main.class:?]
Client> 	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[?:1.7.0_79]
Client> 	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57) ~[?:1.7.0_79]
Client> 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[?:1.7.0_79]
Client> 	at java.lang.reflect.Method.invoke(Method.java:606) ~[?:1.7.0_79]
Client> 	at net.minecraft.launchwrapper.Launch.launch(Launch.java:134) [launchwrapper-1.9.jar:?]
Client> 	at net.minecraft.launchwrapper.Launch.main(Launch.java:28) [launchwrapper-1.9.jar:?]
Client> If on Windows, make sure to provide all of the necessary dll's as specified in the twitchsdk README. Also, make sure to set the PATH environment variable to point to the directory containing the dll's.
Client> [18:01:25] [Client thread/ERROR]: Couldn't initialize twitch stream
Client> [18:01:26] [Client thread/INFO] [MinecraftForge]: Attempting early MinecraftForge initialization
Client> [18:01:26] [Client thread/INFO] [FML]: MinecraftForge v10.13.0.1208 Initialized
Client> [18:01:26] [Client thread/INFO] [FML]: Replaced 182 ore recipies
Client> [18:01:26] [Client thread/INFO] [MinecraftForge]: Completed early MinecraftForge initialization
Client> [18:01:26] [Client thread/INFO] [FML]: Searching /home/darcy/minecraftedu/minecraft/mods for mods
Client> [18:01:26] [Client thread/INFO] [FML]: Also searching /home/darcy/minecraftedu/minecraft/mods/1.7.10 for mods
Client> [18:01:29] [Client thread/INFO] [FML]: Forge Mod Loader has identified 4 mods to load
Client> [18:01:30] [Client thread/INFO]: Reloading ResourceManager: Default, FMLFileResourcePack:Forge Mod Loader, FMLFileResourcePack:Minecraft Forge, FMLFileResourcePack:MinecraftEdu, mcedu_resourcepack.zip
Client> [18:01:30] [Client thread/INFO] [FML]: Processing ObjectHolder annotations
Client> [18:01:30] [Client thread/INFO] [FML]: Found 341 ObjectHolder annotations
Client> [18:01:30] [Client thread/INFO] [FML]: Configured a dormant chunk cache size of 0
Client> [18:01:30] [Client thread/INFO] [FML]: Applying holder lookups
Client> [18:01:30] [Client thread/INFO] [FML]: Holder lookups applied
Client> 
Client> Starting up SoundSystem...
Client> Initializing LWJGL OpenAL
Client>     (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
Client> OpenAL initialized.
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/11.ogg does not exist, cannot add it to event minecraft:records.11
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/13.ogg does not exist, cannot add it to event minecraft:records.13
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/blocks.ogg does not exist, cannot add it to event minecraft:records.blocks
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/cat.ogg does not exist, cannot add it to event minecraft:records.cat
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/chirp.ogg does not exist, cannot add it to event minecraft:records.chirp
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/far.ogg does not exist, cannot add it to event minecraft:records.far
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/mall.ogg does not exist, cannot add it to event minecraft:records.mall
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/mellohi.ogg does not exist, cannot add it to event minecraft:records.mellohi
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/stal.ogg does not exist, cannot add it to event minecraft:records.stal
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/strad.ogg does not exist, cannot add it to event minecraft:records.strad
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/wait.ogg does not exist, cannot add it to event minecraft:records.wait
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/records/ward.ogg does not exist, cannot add it to event minecraft:records.ward
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/menu/menu1.ogg does not exist, cannot add it to event minecraft:music.menu
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/menu/menu2.ogg does not exist, cannot add it to event minecraft:music.menu
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/menu/menu3.ogg does not exist, cannot add it to event minecraft:music.menu
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/menu/menu4.ogg does not exist, cannot add it to event minecraft:music.menu
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/calm1.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/calm2.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/calm3.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/hal1.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/hal2.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/hal3.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/hal4.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/nuance1.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/nuance2.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/piano1.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/piano2.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/piano3.ogg does not exist, cannot add it to event minecraft:music.game
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/creative/creative1.ogg does not exist, cannot add it to event minecraft:music.game.creative
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/creative/creative2.ogg does not exist, cannot add it to event minecraft:music.game.creative
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/creative/creative3.ogg does not exist, cannot add it to event minecraft:music.game.creative
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/creative/creative4.ogg does not exist, cannot add it to event minecraft:music.game.creative
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/creative/creative5.ogg does not exist, cannot add it to event minecraft:music.game.creative
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/creative/creative6.ogg does not exist, cannot add it to event minecraft:music.game.creative
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/end/end.ogg does not exist, cannot add it to event minecraft:music.game.end
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/end/boss.ogg does not exist, cannot add it to event minecraft:music.game.end.dragon
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/end/credits.ogg does not exist, cannot add it to event minecraft:music.game.end.credits
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/nether/nether1.ogg does not exist, cannot add it to event minecraft:music.game.nether
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/nether/nether2.ogg does not exist, cannot add it to event minecraft:music.game.nether
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/nether/nether3.ogg does not exist, cannot add it to event minecraft:music.game.nether
Client> [18:01:31] [Client thread/WARN]: File minecraft:sounds/music/game/nether/nether4.ogg does not exist, cannot add it to event minecraft:music.game.nether
Client> ---- Minecraft Crash Report ----
Client> // But it works on my machine.
Client> 
Client> Time: 4/27/15 6:01 PM
Client> Description: Registering texture
Client> 
Client> org.lwjgl.LWJGLException: X Error - disp: 0x7f4b74ad8800 serial: 148 error: GLXBadRenderRequest request_code: 148 minor_code: 1
Client> 	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:321)
Client> 	at org.lwjgl.opengl.GL11.nglGenTextures(Native Method)
Client> 	at org.lwjgl.opengl.GL11.glGenTextures(GL11.java:1407)
Client> 	at net.minecraft.client.renderer.texture.TextureUtil.func_110996_a(SourceFile:57)
Client> 	at net.minecraft.client.renderer.texture.AbstractTexture.func_110552_b(SourceFile:9)
Client> 	at net.minecraft.client.renderer.texture.SimpleTexture.func_110551_a(SourceFile:48)
Client> 	at net.minecraft.client.renderer.texture.TextureManager.func_110579_a(SourceFile:72)
Client> 	at net.minecraft.client.renderer.texture.TextureManager.func_110577_a(SourceFile:40)
Client> 	at net.minecraft.client.gui.FontRenderer.<init>(FontRenderer.java:73)
Client> 	at net.minecraft.client.Minecraft.func_71384_a(Minecraft.java:488)
Client> 	at net.minecraft.client.Minecraft.func_99999_d(Minecraft.java:872)
Client> 	at net.minecraft.client.main.Main.main(Main.java:186)
Client> 	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
Client> 	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
Client> 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
Client> 	at java.lang.reflect.Method.invoke(Method.java:606)
Client> 	at net.minecraft.launchwrapper.Launch.launch(Launch.java:134)
Client> 	at net.minecraft.launchwrapper.Launch.main(Launch.java:28)
Client> 
Client> 
Client> A detailed walkthrough of the error, its code path and all known details is as follows:
Client> ---------------------------------------------------------------------------------------
Client> 
Client> -- Head --
Client> Stacktrace:
Client> 	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:321)
Client> 	at org.lwjgl.opengl.GL11.nglGenTextures(Native Method)
Client> 	at org.lwjgl.opengl.GL11.glGenTextures(GL11.java:1407)
Client> 	at net.minecraft.client.renderer.texture.TextureUtil.func_110996_a(SourceFile:57)
Client> 	at net.minecraft.client.renderer.texture.AbstractTexture.func_110552_b(SourceFile:9)
Client> 	at net.minecraft.client.renderer.texture.SimpleTexture.func_110551_a(SourceFile:48)
Client> 
Client> -- Resource location being registered --
Client> Details:
Client> 	Resource location: minecraft:textures/font/ascii.png
Client> 	Texture object class: net.minecraft.client.renderer.texture.SimpleTexture
Client> Stacktrace:
Client> 	at net.minecraft.client.renderer.texture.TextureManager.func_110579_a(SourceFile:72)
Client> 	at net.minecraft.client.renderer.texture.TextureManager.func_110577_a(SourceFile:40)
Client> 	at net.minecraft.client.gui.FontRenderer.<init>(FontRenderer.java:73)
Client> 	at net.minecraft.client.Minecraft.func_71384_a(Minecraft.java:488)
Client> 
Client> -- Initialization --
Client> Details:
Client> Stacktrace:
Client> 	at net.minecraft.client.Minecraft.func_99999_d(Minecraft.java:872)
Client> 	at net.minecraft.client.main.Main.main(Main.java:186)
Client> 	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
Client> 	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
Client> 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
Client> 	at java.lang.reflect.Method.invoke(Method.java:606)
Client> 	at net.minecraft.launchwrapper.Launch.launch(Launch.java:134)
Client> 	at net.minecraft.launchwrapper.Launch.main(Launch.java:28)
Client> 
Client> -- System Details --
Client> Details:
Client> 	Minecraft Version: 1.7.10
Client> 	Operating System: Linux (amd64) version 3.13.0-49-generic
Client> 	Java Version: 1.7.0_79, Oracle Corporation
Client> 	Java VM Version: OpenJDK 64-Bit Server VM (mixed mode), Oracle Corporation
Client> 	Memory: 178826040 bytes (170 MB) / 267911168 bytes (255 MB) up to 652738560 bytes (622 MB)
Client> 	JVM Flags: 1 total; -Xmx700m
Client> 	AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
Client> 	IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
Client> 	FML: MCP v9.03 FML v7.10.25.0 Minecraft Forge 10.13.0.1208 4 mods loaded, 4 mods active
Client> 	mcp{9.05} [Minecraft Coder Pack] (minecraft.jar) Unloaded->Constructed->Pre-initialized
Client> 	FML{7.10.25.0} [Forge Mod Loader] (mceduforge-0.jar) Unloaded->Constructed->Pre-initialized
Client> 	Forge{10.13.0.1208} [Minecraft Forge] (mceduforge-0.jar) Unloaded->Constructed->Pre-initialized
Client> 	mcedu{1.7.10} [MinecraftEdu] (mceduforge-0.jar) Unloaded->Constructed->Pre-initialized
Client> 	Launched Version: mceduforge
Client> 	LWJGL: 2.9.1
Client> 	OpenGL: Mesa GLX Indirect GL version 1.3 Mesa 4.0.4, Mesa project: www.mesa3d.org
Client> 	GL Caps: Using GL 1.3 multitexturing.
Client> Not using framebuffer objects because OpenGL 1.4 is not supported, EXT_blend_func_separate is not supported, OpenGL 3.0 is not supported, ARB_framebuffer_object is not supported, and EXT_framebuffer_object is not supported.
Client> Anisotropic filtering is not supported.
Client> Shaders are not available because OpenGL 2.1 is not supported, ARB_shader_objects is not supported, ARB_vertex_shader is not supported, and ARB_fragment_shader is not supported.
Client> 
Client> 	Is Modded: Definitely; Client brand changed to 'fml,forge'
Client> 	Type: Client (map_client.txt)
Client> 	Resource Packs: [mcedu_resourcepack.zip]
Client> 	Current Language: English (US)
Client> 	Profiler Position: N/A (disabled)
Client> 	Vec3 Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
Client> 	Anisotropic Filtering: Off (1)
Client> 
Client> [18:01:31] [Sound Library Loader/INFO]: Sound engine started
Client> #@!@# Game crashed! Crash report saved to: #@!@# /home/darcy/minecraftedu/minecraft/crash-reports/crash-2015-04-27_18.01.31-client.txt
Client> AL lib: (EE) alc_cleanup: 1 device not closed
Game ended with bad state (exit code 255)
Crash report detected, opening: /home/darcy/minecraftedu/minecraft/crash-reports/crash-2015-04-27_18.01.31-client.txt
Ignoring visibility rule and showing launcher due to a game crash
Deleting /home/darcy/minecraftedu/minecraft/versions/mceduforge/mceduforge-natives-102546894157
Couldn't report crash to Mojang
java.io.IOException: Invalid crash report
	at net.minecraft.hopper.HopperService.makeRequest(Unknown Source)
	at net.minecraft.hopper.HopperService.submitReport(Unknown Source)
	at net.minecraft.launcher.ui.tabs.CrashReportTab$1.run(Unknown Source)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:471)
	at java.util.concurrent.FutureTask.run(FutureTask.java:262)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1145)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:615)
	at java.lang.Thread.run(Thread.java:745)

```

---

