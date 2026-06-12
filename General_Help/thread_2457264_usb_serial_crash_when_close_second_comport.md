---
title: "usb serial crash when close second comport"
date: 2021-01-29
forum: General Help
---

### Post by pvttung on 2021-01-29
[COLOR=#172B4D][FONT=-apple-system]Environment: Raspberry Pi 4 installed Ubuntu 20.10 (with the latest updates)[/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]-------------------------------------------[/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]I uses Raspberry Pi 4 to connect to HB-UM43 hub, then connect cp2108 EK USB to serial board to the hub.[/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]After opening connections to both devices, the cp210x driver intermittently crashes on closing the second connection. The problem does not duplicate if opening only one of the connections. Repeatedly opening/closing just the first device works fine. Repeatedly opening/closing just the second device works fine. Opening both, and then trying to close both can trigger the issue. It doesn’t matter what ordered they are opened or closed; closing down the second one can trigger the issue.[/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]I has also realized the same test with our cp2108 boards and the results are: [/FONT][/COLOR]

[LIST]
[*]If I connects the Pi directly to the cp2108 boards, the problem does not happen.
[/LIST]

[LIST]
[*]If he uses an Raspberry Pi 4 connected to cp2108 boards through the HB-UM43 hub, the problem DOES happen.
[/LIST]
[COLOR=#172B4D][FONT=-apple-system]I has also tried modifying cp210x driver downloaded form silabs web site, and i thinks the problem is rooted in cp210x_close() function as i explains [/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]"This is the cp210x_close() call from the cp210x driver:[/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system] [/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]static void cp210x_close(struct usb_serial_port *port)[/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]{ struct cp210x_port_private *port_priv = usb_get_serial_port_data(port);   usb_serial_generic_close(port);   /* Clear both queues; cp2108 needs this to avoid an occasional hang */ cp210x_write_u16_reg(port, CP210X_PURGE, PURGE_ALL);   cp210x_write_u16_reg(port, CP210X_IFC_ENABLE, UART_DISABLE);   /* Disabling the interface disables event-insertion mode. */ port_priv->event_mode = false; }[/FONT][/COLOR][COLOR=#172B4D][FONT=-apple-system] [/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]It does basically four things: cancel any pending transactions on the BULK OUT and IN endpoints plus clear the OUT fifo (usb_serial_generic_close() call), send a request to clear the transmit and receive queues (CP210X_PURGE, PURGE_ALL), send a request to disable the UART (CP210X_IFC_ENABLE, UART_DISABLE), and then flag that the event_mode is off.[/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system] [/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]The issue occurs during the ***usb_serial_generic_close()*** call. Note that this call doesn’t seem to actually close the port handle, but just does some cleanup in preparation for the close. The actual binary for this call comes from the OS; it is linked into the driver.[/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system] [/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]The driver also recovers if you unbind then bind the driver to the device. So it appears this is a software issue and not the silicon getting hung."[/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system] [/FONT][/COLOR]
[COLOR=#172B4D][FONT=-apple-system]Question: Does the removal of this line of code have any side effect? (e.g: make driver unstable, etc?), or is it an issue of the OS, how i can fix this?.

[/FONT][/COLOR]

---

