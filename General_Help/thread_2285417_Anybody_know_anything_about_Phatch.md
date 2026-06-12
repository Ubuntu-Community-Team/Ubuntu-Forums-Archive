---
title: "Anybody know anything about Phatch?"
date: 2015-07-05
forum: General Help
---

### Post by john409 on 2015-07-05
I installed Phatch on a new computer, with Ubuntu 15.04 and it isnt working right.

I was using Ubuntu 14.04 and it worked great to watermark batches of images. But now when I bring up the Watermark menu, the choice to pick a watermark only shows "Mark: PhatchSmall" with no image, when I click on it to assign my image it says "loading" until I move my cursor away. When I try to run the batch using the default image, because I cannot change it, it errors.

Here is the error report:

Error 0:Can not apply action Watermark on image '9-b.jpg' in folder:
/home/smart/Desktop/DEMERS/Catagory Images/Parts Images No Watermark/10


'transparency'


Action:{'fields': {'Horizontal Justification': 'Middle',
            'Horizontal Offset': '50%',
            'Mark': 'Phatch Small',
            'Method': 'Scale',
            'Offset': '5%',
            'Opacity': u'100',
            'Orientation': u'Normal',
            'Position': 'Center',
            'Vertical Justification': 'Middle',
            'Vertical Offset': '50%',
            '__enabled__': 'yes'},
 'label': 'Watermark'}


Traceback (most recent call last):
  File "/usr/share/phatch/phatch/core/api.py", line 614, in apply_action_to_photo
    photo = action.apply(photo, read_only_settings, cache)
  File "/usr/share/phatch/phatch/core/models.py", line 106, in apply
    photo.get_layer().apply_pil(self.pil, **values)
  File "/usr/share/phatch/phatch/core/pil.py", line 750, in apply_pil
    self.image = function(self.image, *arg, **keyw)
  File "/usr/share/phatch/phatch/actions/watermark.py", line 45, in watermark
    orientation, opacity)
  File "/usr/share/phatch/phatch/lib/imtools.py", line 274, in generate_layer
    mark = convert_safe_mode(open_image(mark))
  File "/usr/share/phatch/phatch/lib/imtools.py", line 826, in convert_safe_mode
    del img.info['transparency']
KeyError: 'transparency'
*

Any clues? I have tried uninstalling and reinstalling Phatch several times with the same outcome.

---

### Post by john409 on 2015-07-12
bump

---

### Post by Vladlenin5000 on 2015-07-12
Phatch hasn't been updated in ages and the last forum activity is from 4 years ago...
Definitely NOT looking good.

Breakage should be expected when trying to use software from +5 years ago in a current kernel/system, even when it installs without further complaints.
That said, the software is still being offered in the Ubuntu Software Centre... Have you installed from there (or by any other method but from the official repositories) or did you installed the .deb from the website?

---

### Post by john409 on 2015-07-14
I was running it fine on my laptop with 14.04, but I put 15.04 on my desktop, maybe that is my issue?

---

