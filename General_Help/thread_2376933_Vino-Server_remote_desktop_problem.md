---
title: "Vino-Server remote desktop problem"
date: 2017-11-07
forum: General Help
---

### Post by redrabbit on 2017-11-07
I've just set up a very simple home server for files, messing about with and some media streaming.  Just basic stuff.  

My idea is to have the server sitting without a graphics card, behind a cupboard, and just plugged into power+network that's it.  If there's any reason to reboot, I can do so remotely, and the computer will come back online and I can again SSH in and also use remote desktop.

Well...

I have vino-server running and it works well.  However.  If I close the service down and try to restart it from command line it just doesn't work.  

ssh to server as my local username
export DISPLAY=0.0
/usr/lib/vino/vino-server  (tried & on the end too)

This doesn't work though and VNC viewer in windows just states that the connection is refused.  It's only if I go back into the server itself and restart it does it actually work.  

I've found a few similar threads but none seem to provide the solution and area also older and relating to slightly different circumstances.

Can anyone assist here?

Thanks,

---

