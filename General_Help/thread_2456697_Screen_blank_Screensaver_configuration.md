---
title: "Screen blank Screensaver configuration"
date: 2021-01-17
forum: General Help
---

### Post by Freiklite on 2021-01-17
Hi,
My screen is blank after five minutes without  any action.

In /usr/bin/xfce4-screensaver-configure  file I found:
```
 def parse_internal(self):
         options = OrderedDict()
         if self.name == "xfce-blank":
             options["dpms-sleep-after"] = {'id': 'dpms-sleep-after', 'type': 'slider',
                                            'label': _('After blanking, put display to sleep after'),
                                            'default': 5, 'low': 0, 'high': 60, 'step': 1,
                                            'low-label': _('Never'), 'high-label': _('60 minutes')}
             options["dpms-off-after"] = {'id': 'dpms-off-after', 'type': 'slider',
                                          'label': _('After sleeping, switch display off after'),
                                          'default': 15, 'low': 0, 'high': 60, 'step': 1,
                                          'low-label': _('Never'), 'high-label': _('60 minutes')}
  
```

Can I change options["dpms-sleep-after]={                'default':5    } without risk.

Thank you very much for any suggestion,
Ciao

---

### Post by Freiklite on 2021-01-18
Hi,
I wrote:> options["dpms-sleep-after"] = {'id': 'dpms-sleep-after', 'type': 'slider',
                                            'label': _('After blanking, put display to sleep after'),
                                            'default': **10**,
The screen is blank after 10 minutes but there is no more unlock screen.
Press the space key is enough.
Ciao

---

