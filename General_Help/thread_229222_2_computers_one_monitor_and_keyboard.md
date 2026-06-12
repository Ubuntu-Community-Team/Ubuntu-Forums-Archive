---
title: "2 computers one monitor and keyboard"
date: 2006-08-04
forum: General Help
---

### Post by mikeymouse on 2006-08-04
Does anyone know a way of connecting 2 computers with one monitor and keyboard and mouse?
 Each computer has a different operating system.
thanks mikeymouse

---

### Post by hainesr on 2006-08-04
Try synergy. It's in one of the repos (universe probably).

I use it like this: Ubuntu  (host machine with mouse and keyboard attached)
                    Windows (client)

I have to switch the monitor inputs to see the windows box, of course, but otherwise I'm really pleased with it. I have two inputs on the monitor so it's not a huge issue.

Another solution would be VNC (also in the repos somewhere).

If you fancy a hardware solution, get a KVM (Belkin make them). You only need one input on your monitor and it's then just one button push (or one magic keyboard push) to switch all three in one go.

Cheers,
Rob

---

### Post by CameronCalver on 2006-08-04
I have heard that those kvm's are really good and vnc would be a good software solution but i dont think it would be as good as a kvm becuase there are quicker and not very expensive

---

### Post by eXisor on 2006-08-04
I use x11vnc to manage a headless system. Works great.

---

### Post by nix4me on 2006-08-04
Get a KVM switch.  Research them carefully because some don't work with linux very well.

nix4me

---

### Post by mikeymouse on 2006-08-04
Thanks all,I have already ordered the kvm switch from NCIX and hope to have it within a week..
 Much appreciated.. mikeymouse

---

### Post by djsroknrol on 2006-08-04
I recently built a win box for one of my boys and tested the network with a KVM switch between my Ubuntu box and the MS box...the only advice I can give is to make sure you're on the right box with the KVM before you start the box as the video drivers don't like switching between boxes after starting them...

---

