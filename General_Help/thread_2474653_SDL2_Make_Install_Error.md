---
title: "SDL2 Make Install Error"
date: 2022-05-04
forum: General Help
---

### Post by matthew-cats-dogs on 2022-05-04
I am using Ubuntu Desktop 22.04 and I recently tried './configure; make; make install' from inside the correct SDL2 package diredtory, inside the terminal, to install SDL2 but when the process arrived at 'make install' I got the error: [Makefile:171: install-bin] Error 1. The error message was: "/usr/bin/install: cannot create regular file '/usr/local/bin/sdl2-config': permission denied." I just wanted to report the bug to the Ubuntu community so it can hopefully be fixed.

---

### Post by deadflowr on 2022-05-05
Install needs to be run as root are you running as root or using sudo?
like
```
sudo make install
```

---

### Post by Impavidus on 2022-05-05
When you want to install something in /usr/local, you need root permission. It's no bug; it's a feature.

However, you skipped a few steps in your post. You ran that command presumably because you want to install sdl2 from source and downloaded the source code. Correct? Why? Sdl2 can be installed from the official repositories.

---

### Post by matthew-cats-dogs on 2022-05-05
> **deadflowr said:**
> Install needs to be run as root are you running as root or using sudo?
like
```
sudo make install
```

Thanks! I will try 'sudo make install' rather than 'make install.' I am running as sudo.

---

### Post by matthew-cats-dogs on 2022-05-05
> **Impavidus said:**
> When you want to install something in /usr/local, you need root permission. It's no bug; it's a feature.

However, you skipped a few steps in your post. You ran that command presumably because you want to install sdl2 from source and downloaded the source code. Correct? Why? Sdl2 can be installed from the official repositories.

I could try installing sdl2 from the official repository. I was originally installing sdl2 from the source code because it was what occurred to me first.

---

### Post by Impavidus on 2022-05-06
We see installing from source code as a last resort. If you install a library through the package manager, the package manager will be aware of it and correctly handle things when you install other packages that depend on the same library. Furthermore, you'll get upgrades automatically when they are released and you can cleanly remove the software when no longer needed.

---

### Post by ActionParsnip on 2022-05-06
You can use check-install to make a deb of your efforts. It'll gel better with the rest of the OS as well.

---

### Post by matthew-cats-dogs on 2022-05-06
> **Impavidus said:**
> We see installing from source code as a last resort. If you install a library through the package manager, the package manager will be aware of it and correctly handle things when you install other packages that depend on the same library. Furthermore, you'll get upgrades automatically when they are released and you can cleanly remove the software when no longer needed.

I understand. I installed SDL2 using the official repository by using: 'sudo apt-get install build-essential libsdl2-dev' and then: 'sudo apt-get install libsdl2-image-dev libsdl2-gfx-dev  libsdl2-ttf-dev libsdl2-mixer-dev' Thank you!

---

### Post by matthew-cats-dogs on 2022-05-07
> **ActionParsnip said:**
> You can use check-install to make a deb of your efforts. It'll gel better with the rest of the OS as well.

Thanks, but I will stick with the official repository.

---

