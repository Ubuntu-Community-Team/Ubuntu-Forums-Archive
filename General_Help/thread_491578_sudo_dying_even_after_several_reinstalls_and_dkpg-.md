---
title: "sudo dying even after several reinstalls and dkpg-reconfigures"
date: 2007-07-03
forum: General Help
---

### Post by Kodfish on 2007-07-03
Halp! my sudo just broke today, I have no idea what caused it. I logged in, and went to update my system seeing as how I haven't used it for about 4 days. The update-manager dies telling me sudo is not working correctly. I cannot give the exact error, seeing as how I am unable to replicate it. I try to open synaptic to update manually, but gksu refuses to even open. Fearing the worst I bust open a terminal and type 'sudo vim'. It dies without any noise and takes me back to the prompt. 'echo $?" gives me 141.

I try to su, this works. Running synaptic works fine, and I reinstall sudo. It still fails. One more reinstall and it works fine. I try the update-manager again, and it gives me the same error as before. I try my reinstalation a few times, but no luck. 'dpkg-reconfigure sudo' give me no luck.

How badly am i shafted? Has anyone had this happen to them before?

---

### Post by Kodfish on 2007-07-03
Never mind, something had reconfigured my sudoers file to allow %admin instead of %wheel to use sudo. i figured it out after accidentaly trying to test sudo while root, and since it worked i grepped around in my configs ore carefully.

kthnxbai!

---

