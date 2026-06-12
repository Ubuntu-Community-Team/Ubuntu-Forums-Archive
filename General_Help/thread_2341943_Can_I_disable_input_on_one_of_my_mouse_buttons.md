---
title: "Can I disable input on one of my mouse buttons?"
date: 2016-11-02
forum: General Help
---

### Post by Evil Wayz on 2016-11-02
My new mouse is one of those gaming mouses with extra buttons.  I have a left button, a middlie button/scroll wheel, and a right button.  On the left side there is a page forward and page backward button.  I keep inadvertently hitting the pageback button.  I would like to disable it using xinput set-button-map but if I do it wrong my mouse will be unusuable.  I was wondering if there was a gui for mouse mapping, or if i could figure out which button is what before i remap.

Here is my mouse info:

```

wolf@shaitan:~$ xinput list | grep 'id='
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SiliconWin mouse                        	id=8	[slave  pointer  (2)]
&#9116;   &#8627; SONiX SI Gaming Keyboard                	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; SONiX SI Gaming Keyboard                	id=9	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=11	[slave  keyboard (3)]

```

Running 16.04.1 LTS with 4.7.2 kernel and xubuntu desktop.

---

