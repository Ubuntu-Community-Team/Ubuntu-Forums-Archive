---
title: "how do I create a patch?"
date: 2007-12-21
forum: General Help
---

### Post by skychris on 2007-12-21
Hello all :)

I have some problem with an "USB to Serial" adapter and through my web search, I came across a patch that could solve my problem. The thing is that I'm fairly new at Linux and I don't know what to do to create the patch, as the source I have is in plain text .

the source for the patch is here :

[HTML]http://groups.google.com/group/fa.linux.kernel/msg/337b6ae017a303ab?[/HTML]

Could somebody help me through the steps of applying this patch?

Thanks 

Chris

---

### Post by Trinexx on 2007-12-21
I spent a few minutes trying to figure out how to boil this down, but I think it would be best if you read this entire page, and proceeded from there.

[http://www.cpqlinux.com/patch.html](http://www.cpqlinux.com/patch.html)

Sorry I couldn't be of more help.

---

### Post by skychris on 2007-12-21
Thanks Trinexx,

it's a good start, it's what I was looking for, but before I start playing with my kernel I think I'll do a little bit more reading, so I don't mess up everything :)

---

### Post by skychris on 2007-12-22
bump

... I'm still struggling to find a complete doc or "how to"... if I can get some help, it would be awesome:)..

---

### Post by skychris on 2007-12-23
... I understand that nobody wants to be morally responsible of the frying of my kernel by giving me some advices :lolflag: but If somebody could just have a look at the patch to tell me if it looks safe to patch and if it could be "unpatched" eventually...

thanks again and Merry Christmas 

here it is...
```
--- linux-2.6.22.5/Documentation/usb/usb-serial.txt     2007-08-23
01:23:54.000000000 +0200
+++ linux-2.6.22.5-cc/Documentation/usb/usb-serial.txt  2007-09-14
14:13:28.000000000 +0200
@@ -428,6 +428,19 @@
   See http://www.uuhaus.de/linux/palmconnect.html for up-to-date
   information on this driver.

+Winchiphead CH341 Driver
+
+  This driver is for the Winchiphead CH341 USB-RS232 Converter. This chip
+  also implements an IEEE 1284 parallel port, I2C and SPI, but that is not
+  supported by the driver. The protocol was analyzed from the behaviour
+  of the Windows driver, no datasheet is available at present.
+  The manufacturer's website: http://www.winchiphead.com/.
+  For any questions or problems with this driver, please contact
+  frank <at> kingswood-consulting.co.uk.
+  Extensions for universal baudrate settings and modem status/control has
+  been added by werner <at> cornelius-consult.de.
+
+
 Generic Serial driver

   If your device is not one of the above listed devices, compatible with
--- linux-2.6.22.5/drivers/usb/serial/Kconfig   2007-08-23 01:23:54.000000000
+0200
+++ linux-2.6.22.5-cc/drivers/usb/serial/Kconfig        2007-09-11 11:53:58.000000000
+0200
@@ -92,6 +92,17 @@
          To compile this driver as a module, choose M here: the
          module will be called belkin_sa.

+config USB_SERIAL_CH341
+       tristate "USB Winchiphead CH341 Single Port Serial Driver"
+       depends on USB_SERIAL
+       help
+         Say Y here if you want to use a Winchiphead CH341 single port
+         USB to serial adapter.
+
+         To compile this driver as a module, choose M here: the
+         module will be called ch341.
+
+
 config USB_SERIAL_WHITEHEAT
        tristate "USB ConnectTech WhiteHEAT Serial Driver"
        depends on USB_SERIAL
--- linux-2.6.22.5/drivers/usb/serial/Makefile  2007-08-23 01:23:54.000000000
+0200
+++ linux-2.6.22.5-cc/drivers/usb/serial/Makefile       2007-09-11
11:54:39.000000000 +0200
@@ -15,6 +15,7 @@
 obj-$(CONFIG_USB_SERIAL_AIRPRIME)              += airprime.o
 obj-$(CONFIG_USB_SERIAL_ARK3116)               += ark3116.o
 obj-$(CONFIG_USB_SERIAL_BELKIN)                        += belkin_sa.o
+obj-$(CONFIG_USB_SERIAL_CH341)                  += ch341.o
 obj-$(CONFIG_USB_SERIAL_CP2101)                        += cp2101.o
 obj-$(CONFIG_USB_SERIAL_CYBERJACK)             += cyberjack.o
 obj-$(CONFIG_USB_SERIAL_CYPRESS_M8)            += cypress_m8.o
--- linux-2.6.22.5/drivers/usb/serial/ch341.c   1970-01-01 01:00:00.000000000
+0100
+++ linux-2.6.22.5-cc/drivers/usb/serial/ch341.c        2007-09-14 13:43:28.000000000
+0200
@@ -0,0 +1,579 @@
+/*
+ * Copyright 2007, Frank A Kingswood <frank <at> kingswood-consulting.co.uk>
+ *
+ * Copyright 2007, Werner Cornelius <werner <at> cornelius-consult.de>
+ * for changes/extenions regarding universal baud rate capability and modem
+ * line control/status routines.
+ *
+ * ch341.c implements a serial port driver for the Winchiphead CH341.
+ *
+ * The CH341 device can be used to implement an RS232 asynchronous
+ * serial port, an IEEE-1284 parallel printer port or a memory-like
+ * interface. In all cases the CH341 supports an I2C interface as well.
+ * This driver only supports the asynchronous serial interface.
+ *
+ * This program is free software; you can redistribute it and/or
+ * modify it under the terms of the GNU General Public License version
+ * 2 as published by the Free Software Foundation.
+ */
+
+#include <linux/kernel.h>
+#include <linux/init.h>
+#include <linux/tty.h>
+#include <linux/module.h>
+#include <linux/usb.h>
+#include <linux/usb/serial.h>
+#include <linux/serial.h>
+
+#define DEFAULT_BAUD_RATE 9600
+#define DEFAULT_TIMEOUT   1000
+
+/* flags for IO-Bits */
+#define CH341_BIT_RTS (1 << 6)
+#define CH341_BIT_DTR (1 << 5)
+
+/******************************/
+/* interrupt pipe definitions */
+/******************************/
+/* always 4 interrupt bytes */
+/* first irq byte normally 0x08 */
+/* second irq byte base 0x7d + below */
+/* third irq byte base 0x94 + below */
+/* fourth irq byte normally 0xee */
+
+/* second interrupt byte */
+#define CH341_MULT_STAT 0x04 /* multiple status since last interrupt event */
+
+/* status returned in third interrupt answer byte, inverted in data from irq
*/
+#define CH341_BIT_CTS 0x01
+#define CH341_BIT_DSR 0x02
+#define CH341_BIT_RI  0x04
+#define CH341_BIT_DCD 0x08
+#define CH341_BITS_MODEM_STAT 0x0f /* all bits */
+
+/*******************************/
+/* baudrate calculation factor */
+/*******************************/
+#define CH341_BAUDBASE_FACTOR 1532620800
+#define CH341_BAUDBASE_DIVMAX 3
+
+static int debug;
+
+static struct usb_device_id id_table [] = {
+       { USB_DEVICE(0x4348, 0x5523) },
+       { },
+};
+MODULE_DEVICE_TABLE(usb, id_table);
+
+struct ch341_private {
+    spinlock_t lock; /* access lock */
+    wait_queue_head_t delta_msr_wait; /* wait queue for modem status */    
+    unsigned baud_rate; /* set baud rate */
+    u8 line_control; /* set line control value RTS/DTR */
+    u8 line_status; /* active status of modem control inputs */
+    u8 multi_status_change; /* status changed multiple since last call */
+};
+
+static int ch341_control_out(struct usb_device *dev, u8 request,
+                            u16 value, u16 index)
+{
+       int r;
+       dbg("ch341_control_out(%02x,%02x,%04x,%04x)", USB_DIR_OUT|0x40,
+               (int)request, (int)value, (int)index);
+
+       r = usb_control_msg(dev, usb_sndctrlpipe(dev, 0), request,
+                           USB_TYPE_VENDOR | USB_RECIP_DEVICE | USB_DIR_OUT,
+                           value, index, NULL, 0, DEFAULT_TIMEOUT);
+
+       return r;
+}
+
+static int ch341_control_in(struct usb_device *dev,
+                           u8 request, u16 value, u16 index,
+                           char *buf, unsigned bufsize)
+{
+       int r;
+       dbg("ch341_control_in(%02x,%02x,%04x,%04x,%p,%u)", USB_DIR_IN|0x40,
+               (int)request, (int)value, (int)index, buf, (int)bufsize);
+
+       r = usb_control_msg(dev, usb_rcvctrlpipe(dev, 0), request,
+                           USB_TYPE_VENDOR | USB_RECIP_DEVICE | USB_DIR_IN,
+                           value, index, buf, bufsize, DEFAULT_TIMEOUT);
+       return r;
+}
+
+int ch341_set_baudrate(struct usb_device *dev, struct ch341_private *priv)
+{
+       short a, b;
+       int r;
+       unsigned long factor;
+       short divisor;
+
+       dbg("ch341_set_baudrate(%d)", priv->baud_rate);
+
+       if (!priv->baud_rate)
+          return -EINVAL;
+      
+       factor = (CH341_BAUDBASE_FACTOR / priv->baud_rate);
+       divisor = CH341_BAUDBASE_DIVMAX;
+
+       while ((factor > 0xfff0) && divisor) {
+          factor >>= 3;
+          divisor--;
+       }
+
+       if (factor > 0xfff0)
+          return -EINVAL;
+
+       factor = 0x10000 - factor;
+       a = (factor & 0xff00) | divisor;
+       b = factor & 0xff;
+
+       r = ch341_control_out(dev, 0x9a, 0x1312, a);
+       if (!r)
+               r = ch341_control_out(dev, 0x9a, 0x0f2c, b);
+
+       return r;
+}
+
+int ch341_set_handshake(struct usb_device *dev, u8 control)
+{
+       dbg("ch341_set_handshake(0x%02x)", control);
+       return ch341_control_out(dev, 0xa4, ~control, 0);
+}
+
+int ch341_get_status(struct usb_device *dev, struct ch341_private *priv)
+{
+       char *buffer;
+       int r;
+       const unsigned size = 8;
+       unsigned long flags;
+
+       dbg("ch341_get_status()");
+
+       buffer = kmalloc(size, GFP_KERNEL);
+       if (!buffer)
+               return -ENOMEM;
+
+       r = ch341_control_in(dev, 0x95, 0x0706, 0, buffer, size);
+       if ( r < 0)
+               goto out;
+
+       /* setup the private status if available */
+       if (r == 2) {
+          r = 0;
+          spin_lock_irqsave(&priv->lock, flags);
+          priv->line_status = (~(*buffer)) & CH341_BITS_MODEM_STAT;
+          priv->multi_status_change = 0;
+          spin_unlock_irqrestore(&priv->lock, flags);
+       } else
+          r = -EPROTO;      
+
+out:   kfree(buffer);
+       return r;
+}
+
+/* --------------------------------------------------------------------------
*/
+
+int ch341_configure(struct usb_device *dev, struct ch341_private *priv)
+{
+       char *buffer;
+       int r;
+       const unsigned size = 8;
+
+       dbg("ch341_configure()");
+
+       buffer = kmalloc(size, GFP_KERNEL);
+       if (!buffer)
+               return -ENOMEM;
+
+       /* expect two bytes 0x27 0x00 */
+       r = ch341_control_in(dev, 0x5f, 0, 0, buffer, size);
+       if (r < 0)
+               goto out;
+
+       r = ch341_control_out(dev, 0xa1, 0, 0);
+       if (r < 0)
+               goto out;
+
+       r = ch341_set_baudrate(dev, priv);
+       if (r < 0)
+               goto out;
+
+       /* expect two bytes 0x56 0x00 */
+       r = ch341_control_in(dev, 0x95, 0x2518, 0, buffer, size);
+       if (r < 0)
+               goto out;
+
+       r = ch341_control_out(dev, 0x9a, 0x2518, 0x0050);
+       if (r < 0)
+               goto out;
+
+       /* expect 0xff 0xee */
+       r = ch341_get_status(dev, priv);
+       if (r < 0)
+               goto out;
+
+       r = ch341_control_out(dev, 0xa1, 0x501f, 0xd90a);
+       if (r < 0)
+               goto out;
+
+       r = ch341_set_baudrate(dev, priv);
+       if (r < 0)
+               goto out;
+
+       r = ch341_set_handshake(dev, priv->line_control);
+       if (r < 0)
+               goto out;
+
+       /* expect 0x9f 0xee */
+       r = ch341_get_status(dev, priv);
+
+out:   kfree(buffer);
+       return r;
+}
+
+/* allocate private data */
+static int ch341_attach(struct usb_serial *serial)
+{
+       struct ch341_private *priv;
+       int r;
+
+       dbg("ch341_attach()");
+
+       /* private data */
+       priv = kzalloc(sizeof(struct ch341_private), GFP_KERNEL);
+       if (!priv)
+               return -ENOMEM;
+
+       spin_lock_init(&priv->lock);
+       init_waitqueue_head(&priv->delta_msr_wait);
+       priv->baud_rate = DEFAULT_BAUD_RATE;
+       priv->line_control = CH341_BIT_RTS | CH341_BIT_DTR;
+
+       r = ch341_configure(serial->dev, priv);
+       if (r < 0)
+               goto error;
+
+       usb_set_serial_port_data(serial->port[0], priv);
+       return 0;
+
+error: kfree(priv);
+       return r;
+}
+
+static void ch341_close(struct usb_serial_port *port, struct file *filp)
+{
+       struct ch341_private *priv = usb_get_serial_port_data(port);
+       unsigned long flags;
+       unsigned int c_cflag;
+
+       dbg("%s - port %d", __FUNCTION__, port->number);
+
+       /* shutdown our urbs */
+       dbg("%s - shutting down urbs", __FUNCTION__);
+       usb_kill_urb(port->write_urb);
+       usb_kill_urb(port->read_urb);
+       usb_kill_urb(port->interrupt_in_urb);
+
+       if (port->tty) {
+               c_cflag = port->tty->termios->c_cflag;
+               if (c_cflag & HUPCL) {
+                       /* drop DTR and RTS */
+                       spin_lock_irqsave(&priv->lock, flags);
+                       priv->line_control = 0;
+                       spin_unlock_irqrestore(&priv->lock, flags);
+                       ch341_set_handshake(port->serial->dev, 0);
+               }
+       }
+       wake_up_interruptible(&priv->delta_msr_wait);
+}
+
+/* open this device, set default parameters */
+static int ch341_open(struct usb_serial_port *port, struct file *filp)
+{
+       struct usb_serial *serial = port->serial;
+       struct ch341_private *priv =
usb_get_serial_port_data(serial->port[0]);
+       int r;
+
+       dbg("ch341_open()");
+
+       priv->baud_rate = DEFAULT_BAUD_RATE;
+       priv->line_control = CH341_BIT_RTS | CH341_BIT_DTR;
+
+       r = ch341_configure(serial->dev, priv);
+       if (r)
+               goto out;
+
+       r = ch341_set_handshake(serial->dev, priv->line_control);
+       if (r)
+               goto out;
+
+       r = ch341_set_baudrate(serial->dev, priv);
+       if (r)
+               goto out;
+
+       dbg("%s - submitting interrupt urb", __FUNCTION__);
+       port->interrupt_in_urb->dev = serial->dev;
+       r = usb_submit_urb(port->interrupt_in_urb, GFP_KERNEL);
+       if (r) {
+          dev_err(&port->dev, "%s - failed submitting interrupt urb,"
+                  " error %d\n", __FUNCTION__, r);
+          ch341_close(port, NULL);
+          return -EPROTO;
+       }
+
+       r = usb_serial_generic_open(port, filp);
+
+out:   return r;
+}
+
+/* Old_termios contains the original termios settings and
+ * tty->termios contains the new setting to be used.
+ */
+static void ch341_set_termios(struct usb_serial_port *port,
+                             struct ktermios *old_termios)
+{
+       struct ch341_private *priv = usb_get_serial_port_data(port);
+       struct tty_struct *tty = port->tty;
+       unsigned baud_rate;
+       unsigned long flags;
+
+       dbg("ch341_set_termios()");
+
+       if (!tty || !tty->termios)
+               return;
+
+       baud_rate = tty_get_baud_rate(tty);
+       priv->baud_rate = baud_rate;
+
+       if (baud_rate) {
+          spin_lock_irqsave(&priv->lock, flags);
+          priv->line_control |= (CH341_BIT_DTR | CH341_BIT_RTS);      
+          spin_unlock_irqrestore(&priv->lock, flags);      
+          ch341_set_baudrate(port->serial->dev, priv);
+       } else {
+          spin_lock_irqsave(&priv->lock, flags);
+          priv->line_control &= ~(CH341_BIT_DTR | CH341_BIT_RTS);          
+          spin_unlock_irqrestore(&priv->lock, flags);      
+       }
+       ch341_set_handshake(port->serial->dev, priv->line_control);
+
+       /* Unimplemented:
+        * (cflag & CSIZE) : data bits [5, 8]
+        * (cflag & PARENB) : parity {NONE, EVEN, ODD}
+        * (cflag & CSTOPB) : stop bits [1, 2]
+        */
+}
+
+static int ch341_tiocmset(struct usb_serial_port *port, struct file *file,
+                         unsigned int set, unsigned int clear)
+{
+       struct ch341_private *priv = usb_get_serial_port_data(port);
+       unsigned long flags;
+       u8 control;
+
+       spin_lock_irqsave(&priv->lock, flags);
+       if (set & TIOCM_RTS)
+               priv->line_control |= CH341_BIT_RTS;
+       if (set & TIOCM_DTR)
+               priv->line_control |= CH341_BIT_DTR;
+       if (clear & TIOCM_RTS)
+               priv->line_control &= ~CH341_BIT_RTS;
+       if (clear & TIOCM_DTR)
+               priv->line_control &= ~CH341_BIT_DTR;
+       control = priv->line_control;
+       spin_unlock_irqrestore(&priv->lock, flags);
+
+       return(ch341_set_handshake(port->serial->dev, control));
+}
+
+static void ch341_read_int_callback(struct urb *urb)
+{
+       struct usb_serial_port *port = (struct usb_serial_port *) urb->context;
+       unsigned char *data = urb->transfer_buffer;
+       unsigned int actual_length = urb->actual_length;
+       int status;
+
+       dbg("%s (%d)", __FUNCTION__, port->number);
+
+       switch (urb->status) {
+       case 0:
+               /* success */
+               break;
+       case -ECONNRESET:
+       case -ENOENT:
+       case -ESHUTDOWN:
+               /* this urb is terminated, clean up */
+               dbg("%s - urb shutting down with status: %d", __FUNCTION__,
+                   urb->status);
+               return;
+       default:
+               dbg("%s - nonzero urb status received: %d", __FUNCTION__,
+                   urb->status);
+               goto exit;
+       }
+
+       usb_serial_debug_data(debug, &port->dev, __FUNCTION__,
+                             urb->actual_length, urb->transfer_buffer);
+
+       if (actual_length >= 4) {
+           struct ch341_private *priv = usb_get_serial_port_data(port);
+           unsigned long flags;
+
+           spin_lock_irqsave(&priv->lock, flags);
+           priv->line_status = (~(data[2])) & CH341_BITS_MODEM_STAT;
+           if ((data[1] & CH341_MULT_STAT))
+               priv->multi_status_change = 1;
+           spin_unlock_irqrestore(&priv->lock, flags);
+           wake_up_interruptible(&priv->delta_msr_wait);
+       }
+
+exit:
+       status = usb_submit_urb(urb, GFP_ATOMIC);
+       if (status)
+               dev_err(&urb->dev->dev,
+                       "%s - usb_submit_urb failed with result %d\n",
+                       __FUNCTION__, status);
+}
+
+static int wait_modem_info(struct usb_serial_port *port, unsigned int arg)
+{
+       struct ch341_private *priv = usb_get_serial_port_data(port);
+       unsigned long flags;
+       u8 prevstatus;
+       u8 status;
+       u8 changed;
+       u8 multi_change = 0;
+
+       spin_lock_irqsave(&priv->lock, flags);
+       prevstatus = priv->line_status;
+       priv->multi_status_change = 0;
+       spin_unlock_irqrestore(&priv->lock, flags);
+
+       while (!multi_change) {
+               interruptible_sleep_on(&priv->delta_msr_wait);
+               /* see if a signal did it */
+               if (signal_pending(current))
+                       return -ERESTARTSYS;
+
+               spin_lock_irqsave(&priv->lock, flags);
+               status = priv->line_status;
+               multi_change = priv->multi_status_change;
+               spin_unlock_irqrestore(&priv->lock, flags);
+
+               changed=prevstatus^status;
+
+               if (((arg & TIOCM_RNG) && (changed & CH341_BIT_RI)) ||
+                   ((arg & TIOCM_DSR) && (changed & CH341_BIT_DSR)) ||
+                   ((arg & TIOCM_CD)  && (changed & CH341_BIT_DCD)) ||
+                   ((arg & TIOCM_CTS) && (changed & CH341_BIT_CTS)) ) {
+                       return 0;
+               }
+               prevstatus = status;
+       }
+
+       return 0;
+}
+
+static int ch341_ioctl(struct usb_serial_port *port, struct file *file,
+                       unsigned int cmd, unsigned long arg)
+{
+       dbg("%s (%d) cmd = 0x%04x", __FUNCTION__, port->number, cmd);
+
+       switch (cmd) {
+               case TIOCMIWAIT:
+                       dbg("%s (%d) TIOCMIWAIT", __FUNCTION__,  port->number);
+                       return wait_modem_info(port, arg);
+
+               default:
+                       dbg("%s not supported = 0x%04x", __FUNCTION__, cmd);
+                       break;
+       }
+
+       return -ENOIOCTLCMD;
+}
+
+static int ch341_tiocmget(struct usb_serial_port *port, struct file *file)
+{
+       struct ch341_private *priv = usb_get_serial_port_data(port);
+       unsigned long flags;
+       u8 mcr;
+       u8 status;
+       unsigned int result;
+
+       dbg("%s (%d)", __FUNCTION__, port->number);
+
+       spin_lock_irqsave(&priv->lock, flags);
+       mcr = priv->line_control;
+       status = priv->line_status;
+       spin_unlock_irqrestore(&priv->lock, flags);
+
+       result = ((mcr & CH341_BIT_DTR)             ? TIOCM_DTR : 0)
+                 | ((mcr & CH341_BIT_RTS)  ? TIOCM_RTS : 0)
+                 | ((status & CH341_BIT_CTS)       ? TIOCM_CTS : 0)
+                 | ((status & CH341_BIT_DSR)       ? TIOCM_DSR : 0)
+                 | ((status & CH341_BIT_RI)        ? TIOCM_RI  : 0)
+                 | ((status & CH341_BIT_DCD)       ? TIOCM_CD  : 0);
+
+       dbg("%s - result = %x", __FUNCTION__, result);
+
+       return result;
+}
+
+static struct usb_driver ch341_driver = {
+       .name           = "ch341",
+       .probe          = usb_serial_probe,
+       .disconnect     = usb_serial_disconnect,
+       .id_table       = id_table,
+       .no_dynamic_id  = 1,
+};
+
+static struct usb_serial_driver ch341_device = {
+       .driver = {
+               .owner  = THIS_MODULE,
+               .name   = "ch341-uart",
+       },
+       .id_table         = id_table,
+       .usb_driver       = &ch341_driver,
+       .num_interrupt_in = 1, //NUM_DONT_CARE,
+       .num_bulk_in      = 1,
+       .num_bulk_out     = 1,
+       .num_ports        = 1,
+       .open             = ch341_open,
+       .close            = ch341_close,
+       .ioctl            = ch341_ioctl,
+       .set_termios      = ch341_set_termios,
+       .tiocmget         = ch341_tiocmget,
+       .tiocmset         = ch341_tiocmset,
+       .read_int_callback= ch341_read_int_callback,
+       .attach           = ch341_attach,
+};
+
+static int __init ch341_init(void)
+{
+       int retval;
+
+       retval = usb_serial_register(&ch341_device);
+       if (retval)
+               return retval;
+       retval = usb_register(&ch341_driver);
+       if (retval)
+               usb_serial_deregister(&ch341_device);
+       return retval;
+}
+
+static void __exit ch341_exit(void)
+{
+       usb_deregister(&ch341_driver);
+       usb_serial_deregister(&ch341_device);
+}
+
+module_init(ch341_init);
+module_exit(ch341_exit);
+MODULE_LICENSE("GPL");
+
+module_param(debug, bool, S_IRUGO | S_IWUSR);
+MODULE_PARM_DESC(debug, "Debug enabled or not");
+
+/* EOF ch341.c */


```

---

### Post by skychris on 2007-12-24
...anyone? .... anyone? ..... Bueller?   :)

---

