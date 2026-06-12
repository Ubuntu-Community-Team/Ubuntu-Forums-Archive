---
title: "XFWM4 Error"
date: 2007-08-04
forum: General Help
---

### Post by kadath on 2007-08-04
I booted into Xubuntu today to be greeted with missing window borders.

When I attempt to run xfwm4 from the command line, it spits out this error:

```
** (xfwm4:5616): WARNING **: Specified key theme "Default" missing, using default
missing value for option add_workspace_key
missing value for option cancel_key
missing value for option close_window_key
missing value for option cycle_windows_key
missing value for option del_workspace_key
missing value for option down_workspace_key
missing value for option fullscreen_key
missing value for option hide_window_key
missing value for option left_workspace_key
missing value for option lower_window_key
missing value for option maximize_horiz_key
missing value for option maximize_vert_key
missing value for option maximize_window_key
missing value for option move_window_down_key
missing value for option move_window_down_workspace_key
missing value for option move_window_left_key
missing value for option move_window_left_workspace_key
missing value for option move_window_next_workspace_key
missing value for option move_window_prev_workspace_key
missing value for option popup_menu_key
missing value for option move_window_right_key
missing value for option move_window_right_workspace_key
missing value for option move_window_up_key
missing value for option move_window_up_workspace_key
missing value for option move_window_workspace_1_key
missing value for option move_window_workspace_2_key
missing value for option move_window_workspace_3_key
missing value for option move_window_workspace_4_key
missing value for option move_window_workspace_5_key
missing value for option move_window_workspace_6_key
missing value for option move_window_workspace_7_key
missing value for option move_window_workspace_8_key
missing value for option move_window_workspace_9_key
missing value for option move_window_workspace_10_key
missing value for option move_window_workspace_11_key
missing value for option move_window_workspace_12_key
missing value for option next_workspace_key
missing value for option prev_workspace_key
missing value for option raise_window_key
missing value for option resize_window_down_key
missing value for option resize_window_left_key
missing value for option resize_window_right_key
missing value for option resize_window_up_key
missing value for option right_workspace_key
missing value for option shade_window_key
missing value for option stick_window_key
missing value for option up_workspace_key
missing value for option workspace_1_key
missing value for option workspace_2_key
missing value for option workspace_3_key
missing value for option workspace_4_key
missing value for option workspace_5_key
missing value for option workspace_6_key
missing value for option workspace_7_key
missing value for option workspace_8_key
missing value for option workspace_9_key
missing value for option workspace_10_key
missing value for option workspace_11_key
missing value for option workspace_12_key

** (xfwm4:5616): WARNING **: Missing values in defaults file

** (xfwm4:5616): WARNING **: Missing data from default files
```

Did I accidentally delete a config file or something?

**EDIT:** I accidentally deleted the default xfwm4 theme, which includes the default keythemerc file. Replaced it and everything's okay now.

---

