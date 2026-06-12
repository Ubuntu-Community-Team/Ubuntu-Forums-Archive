---
title: "spontaneous &quot;power off&quot; dialog"
date: 2019-12-25
forum: General Help
---

### Post by jvglynnjr on 2019-12-25
Running Ubuntu 18.04.3 LTS.   While using certain websites to play games, the "power off" dialog keeps popping up, the same one that appears when you click on the power button icon. 

Here's some syslog surrounding the event:

```
Dec 25 14:30:20 Oryx-jvg org.gnome.Shell.desktop[2319]: Window manager warning: Overwriting existing binding of keysym 73 with keysym 73 (keycode 27).Dec 25 14:30:20 Oryx-jvg org.gnome.Shell.desktop[2319]: Window manager warning: last_user_time (105455443) is greater than comparison timestamp (105455412).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Dec 25 14:30:20 Oryx-jvg org.gnome.Shell.desktop[2319]: Window manager warning: 0x3a00003 (Play MathD) appears to be one of the offending windows with a timestamp of 105455443.  Working around...
Dec 25 14:30:23 Oryx-jvg gnome-session-binary[2168]: Entering running state
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Dec 25 14:30:24 Oryx-jvg gnome-system-lo[12323]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Dec 25 14:30:32 Oryx-jvg gnome-session-binary[2168]: Entering running state
Dec 25 14:31:00 Oryx-jvg gnome-session-binary[2168]: Entering running state
Dec 25 14:31:29 Oryx-jvg gnome-session-binary[2168]: Entering running state
Dec 25 14:31:40 Oryx-jvg gnome-session-binary[2168]: Entering running state
Dec 25 14:31:49 Oryx-jvg gnome-shell[2319]: pushModal: invocation of begin_modal failed
Dec 25 14:31:49 Oryx-jvg gnome-session[2168]: gnome-session-binary[2168]: WARNING: Unable to open shell end session dialog: GDBus.Error:org.gnome.Shell.ModalDialog.GrabError: Cannot grab pointer and keyboard
Dec 25 14:31:49 Oryx-jvg gnome-session-binary[2168]: WARNING: Unable to open shell end session dialog: GDBus.Error:org.gnome.Shell.ModalDialog.GrabError: Cannot grab pointer and keyboard
Dec 25 14:31:49 Oryx-jvg gnome-session-binary[2168]: Entering running state



```

Any help appreciated

```
cpu          description: CPU
          product: Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
          vendor: Intel Corp.
          physical id: 26
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 3254MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz



```

---

