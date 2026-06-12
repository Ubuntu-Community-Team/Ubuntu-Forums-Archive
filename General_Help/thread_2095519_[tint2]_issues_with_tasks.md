---
title: "[tint2] issues with tasks"
date: 2012-12-17
forum: General Help
---

### Post by savl0n on 2012-12-17
Hello!

I'm having an issue with tint2. It runs fine and all, it just wont show my current tasks

This is what it looks like with programs open
[IMG]http://i.imgur.com/72Wcj.png[/IMG]



my tint2rc
```
# Background definitions # ID 1 rounded = 0 border_width = 0 background_color = #080808 100 border_color = #3D5454 100  # ID 2 rounded = 0 border_width = 2 background_color = #000000 100 border_color = #FFFFFF 0  # ID 3 rounded = 0 border_width = 1 background_color = #121212 100 border_color = #FFFFFF 0  # ID 4 rounded = 0 border_width = 1 background_color = #000000 100 border_color = #286F8A 100  # Panel panel_monitor = all panel_position = bottom center horizontal panel_size = 100% 20 panel_margin = 0 0 panel_padding = 0 0 0 panel_dock = 0 wm_menu = 0 panel_layer = bottom panel_background_id = 1  # Panel Autohide autohide = 0 autohide_show_timeout = 0.3 autohide_hide_timeout = 2 autohide_height = 2 strut_policy = follow_size  # Taskbar taskbar_mode = single_desktop taskbar_padding = 0 0 1 taskbar_background_id = 0 taskbar_active_background_id = 0  # Tasks urgent_nb_of_blink = 8 task_icon = 0 task_text = 1 task_centered = 1 task_maximum_size = 230 35 task_padding = 1 1 task_background_id = 0 task_active_background_id = 2 task_urgent_background_id = 3 task_iconified_background_id = 0  # Task Icons task_icon_asb = 70 0 0 task_active_icon_asb = 100 0 0 task_urgent_icon_asb = 100 0 0 task_iconified_icon_asb = 70 0 0  # Fonts task_font = cure 10 task_font_color = #719F9F 100 task_active_font_color = #FF6565 100 task_urgent_font_color = #FFFFFF 100 task_iconified_font_color = #606060 100 font_shadow = 0  # System Tray systray = 1 systray_padding = 4 0 5 systray_sort = ascending systray_background_id = 0 systray_icon_size = 15 systray_icon_asb = 100 0 0  # Clock time1_format = %H.%M time1_font = Envy Code R 12 clock_font_color = #FFFFFF 100 clock_padding = 6 1 clock_background_id = 3  # Tooltips tooltip = 1 tooltip_padding = 5 3 tooltip_show_timeout = 0.7 tooltip_hide_timeout = 0.3 tooltip_background_id = 4 tooltip_font = Terminus 8 tooltip_font_color = #286F8A 100  # Mouse mouse_middle = none mouse_right = close mouse_scroll_up = toggle mouse_scroll_down = iconify  # Battery battery = 0 battery_low_status = 10 battery_low_cmd = notify-send "battery low" battery_hide = 98 bat1_font = sans 8 bat2_font = sans 6 battery_font_color = #FFFFFF 73 battery_padding = 1 0 battery_background_id = 0  # End of config
```If I could get some help it would be much appreciated.
And yes, I am new to UF. I hope I can help you out in the future!

[http://pastebin.com/6hstZk9n](http://pastebin.com/6hstZk9n) 
for proper tint2rc formatting

---

