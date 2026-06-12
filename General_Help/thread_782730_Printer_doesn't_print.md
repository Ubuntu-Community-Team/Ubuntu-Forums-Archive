---
title: "Printer doesn't print"
date: 2008-05-05
forum: General Help
---

### Post by tjamtjam on 2008-05-05
Hi!

I'm having problems with my Samsung ML-2010 printer. It doesn't print anything. Ubuntu detectes it fine and jobs go to queue but nothing is printed. The printer has worked before. I think it stopped working when I updated to Ubuntu 8.04. During the update I was asked if I wanted to replace my old CUPS configs or keep the old and I chose to keep the old config.

I ran Printer troubleshooting from printer configuratation and it gave me this:
```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8708280>,
 'cups_instance': None,
 'cups_queue': 'ML-2010',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Samsung/ML-2010',
                       'printer-info': u'Samsung ML-2010',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Samsung ML-2010, 1.0',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/rastertospl2 failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 176196,
                       'printer-uri-supported': u'ipp://localhost:631/printers/ML-2010'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '/usr/lib/cups/filter/rastertospl2 failed',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(49,
                            u'Job stopped due to filter errors; please consult the error_log file for details.')],
 'test_page_job_id': [49],
 'test_page_job_status': [(49, 'ML-2010', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '/usr/lib/cups/filter/rastertospl2 failed',
 'printer-state-reasons': 'none'}

```

Any help would be greatly appreciated!

Edit:
I solved this. I just needed to delete the printer and add it again.

---

