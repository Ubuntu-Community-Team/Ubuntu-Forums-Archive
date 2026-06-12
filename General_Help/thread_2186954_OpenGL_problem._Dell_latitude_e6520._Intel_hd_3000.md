---
title: "OpenGL problem. Dell latitude e6520. Intel hd 3000"
date: 2013-11-10
forum: General Help
---

### Post by markuslaaksonen on 2013-11-10
Hello. I just installed my very first linux distro. Xubuntu 12.04.3. I have dell latitude e6520 computer. Whit intell hd3000 graphics card. Otherwise using xubuntu works very well. But. When i installed steam and tryed to play counter strike source there comes error that says.
This application requires either the GL_EXT_texture_compression_s3tc, or  the GL_EXT_texture_compression_dxt1 + GL_ANGLE_texture_compression_dxt3  + GL_ANGLE_texture_compression_dxt5 OpenGL extensions. Please install  S3TC texture support.
So what i have done so far is what steam adviced to me do. Open Ubuntu Software Center.
    From the top-level menu, select Edit | Software Sources ... .
    Select the Other Software tab.
    Click the Add ... button.
    Enter the following: deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main
    Click the +Add Source button.
    Provide your user password when requested.
    Click the Close button.
     Open Update Manager (click the Unity icon on the launch bar and enter  "update manager") and click the Check button to refresh the package  cache. Done all that. nothing.. still not work. Then what i did was apt-add-repository ppa:glasen/intel-driver
apt-get install --install-recommends linux-generic-lts-quantal xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal
apt-get update
apt-get -y dist-upgrade
glxinfo | grep "OpenGL version" # verify you have mesia 9.1.6  Nothing.. Can someone please help me. or is the only way go back to windows :(. Sry for my bad english.

---

