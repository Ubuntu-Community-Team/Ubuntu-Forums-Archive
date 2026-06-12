---
title: "Festival error: unbound variable"
date: 2007-12-11
forum: General Help
---

### Post by antisho on 2007-12-11
I'm having some trouble with festival. I downloaded the plugin and some voices from
[http://cslu.cse.ogi.edu/tts/download/](http://cslu.cse.ogi.edu/tts/download/)
followed the instructions and recompiled, but now when I run
```
text2wave -eval "(voice_as_diphone)"
```
it spits out
```
SIOD ERROR: unbound variable : OGIdbase.lookup_info
BACKTRACE:
   0: OGIdbase.lookup_info
   1: (if
    (not (boundp (quote prev_dbase_lookup_info)))
    (set! prev_dbase_lookup_info OGIdbase.lookup_info))
   2: (#<CLOSURE nil (begin "(voice_as_diphone)
  Set up the current voice to be an American female AS using the as diphone set." (set! as_diphone_f0_mean 200) (set! as_diphone_f0_std 19) (set! FP_F0 200) (set! ogi_grouped_or_ungrouped (quote grouped)) (set! ogi_resORsinLPC (quote resLPC)) (ogi_configure_voice (quote as_diphone)) (set! OGI_unitsel OGI_diphone_unitsel) (set! ogi_di_alt_L (quote ((m= (m)) (n= (n)) (l= (l)) (h (pau)) (j (i:)) (dx (t d)) (& (^)) (k>9r (k)) (k>w (k)) (k>l (k)) (p>9r (p)) (p>w (p)) (p>l (p)) (t>9r (t)) (t>w (t)) (t>l (t)) (t>9r<s (t>9r t<s t)) (p>9r<s (p>9r p)) (t<s (t)) (pau (?))))) (set! ogi_di_alt_R (quote ((m= (m)) (n= (n)) (l= (l)) (h (pau)) (j (i:)) (dx (t d)) (& (^)) (k>9r (k)) (k>w (k)) (k>l (k)) (p>9r (p)) (p>w (p)) (p>l (p)) (t>9r (t)) (t>w (t)) (t>l (t)) (t>9r<s (t>9r t<s t)) (p>9r<s (p>9r p)) (t<s (t))))) (set! ogi_di_default "pau-h") (set! AccentMaxStart 65) (set! AccentMaxMid 40) (set! AccentMaxEnd 50) (set! AccentQuestion 80) (set! AccentComma2 20) (set! AccentComma3 10) (set! AccentComma4 30) (set! PhraseStart 220) (set! PhraseMid 180) (set! PhraseEnd 140) (set! voicename (quote as_diphone)) (if (string-equal ogi_grouped_or_ungrouped "grouped") (set! ogi_resLPC_analysis_params (list (list (quote dbname) voice_dirname) (list (quote groupfile) (path-append ogi_diphone_dir "group" (string-append voicename "_resLPC.group"))) (quote (data_type "resLPC")) (quote (access_mode "ondemand")))) (set! ogi_resLPC_analysis_params (list (list (quote dbname) voice_dirname) (list (quote unitdic_file) (path-append ogi_diphone_dir "ungrouped" " unittable.ms")) (quote (phoneset "worldbet")) (list (quote base_dir) (path-append ogi_diphone_dir "ungrouped/")) (quote (lpc_dir "lpc/")) (quote (lpc_ext ".lsf")) (quote (exc_dir "lpc/")) (quote (exc_ext ".res")) (quote (pm_dir "pm/")) (quote (pm_ext ".pmv")) (quote (data_type "resLPC")) (quote (access_mode "ondemand")) (quote (samp_freq 22050)) (quote (sig_band 0.01)) (quote (isCompressed "Y")) (quote (preemph 0.96)) (quote (deemphasis 0.99))))) (set! ogi_sinLPC_analysis_params (list (list (quote voicename) voice_dirname) (list (quote groupfile) (path-append ogi_diphone_dir "group" (string-append voicename "_sinLPC.group"))) (quote (access_mode "ondemand")) (quote (useCompressed 0)) (quote (doSinAnalysis 1)))) (if (string-equal ogi_grouped_or_ungrouped "grouped") (set! ogi_sinLPC_analysis_params (append ogi_sinLPC_analysis_params (list (quote (useGrouped 1))))) (set! ogi_sinLPC_analysis_params (append ogi_sinLPC_analysis_params (list (quote (useGrouped 0)) (list (quote unittable_file) (path-append ogi_diphone_dir "ungrouped" " unittable.ms")) (list (quote pmdir) (path-append ogi_diphone_dir "ungrouped" "pm")) (list (quote wavdir) (path-append ogi_diphone_dir "ungrouped" "wav")) (list (quote sinlpcdir) (path-append ogi_diphone_dir "ungrouped" "sinlpc")) (quote (sinlpc_save_format "est_ascii")) (quote (Fs 16000)) (quote (Fvox 4000)) (quote (vuv_filt ((- 0.00265023 0.0426373 0.253502 0.413021 0.253502 0.0426373 -0.00265023) (1)))) (quote (lpcorder 14)) (quote (data_type "sinLPC")) (quote (access_mode "ondemand")) (quote (pre-emph 0.95)) (quote (show_chunk_pms 0)))))) (initialize_OGIsynth))>)
   3: (voice_as_diphone)
   4: (if
    (string-matches (car (cdr o)) "^(.*")
    (eval (read-from-string (car (cdr o))))
    ...)
   5: (if
    (string-equal "-o" (car o))
    (begin
     (if (not (cdr o)) (text2wave_error "no output file specified"))
     (set! outfile (car (cdr o)))
     ...)
    ...)
   6: (begin
    (if
     (string-equal "-o" (car o))
     (...)
     ...)
    (set! o (cdr o)))
   7: (while
    o
    (begin
     (...)
     (set! o (cdr o))))
   8: (get_options)
   9: (main)
  10: (load "/usr/bin/text2wave")
```
and when I try run (voice_as_diphone) in festival itself,
```
SIOD ERROR: unbound variable : OGIdbase.lookup_info
BACKTRACE:
   0: OGIdbase.lookup_info
   1: (if
    (not (boundp (quote prev_dbase_lookup_info)))
    (set! prev_dbase_lookup_info OGIdbase.lookup_info))
   2: (#<CLOSURE nil (begin "(voice_as_diphone)
  Set up the current voice to be an American female AS using the as diphone set." (set! as_diphone_f0_mean 200) (set! as_diphone_f0_std 19) (set! FP_F0 200) (set! ogi_grouped_or_ungrouped (quote grouped)) (set! ogi_resORsinLPC (quote resLPC)) (ogi_configure_voice (quote as_diphone)) (set! OGI_unitsel OGI_diphone_unitsel) (set! ogi_di_alt_L (quote ((m= (m)) (n= (n)) (l= (l)) (h (pau)) (j (i:)) (dx (t d)) (& (^)) (k>9r (k)) (k>w (k)) (k>l (k)) (p>9r (p)) (p>w (p)) (p>l (p)) (t>9r (t)) (t>w (t)) (t>l (t)) (t>9r<s (t>9r t<s t)) (p>9r<s (p>9r p)) (t<s (t)) (pau (?))))) (set! ogi_di_alt_R (quote ((m= (m)) (n= (n)) (l= (l)) (h (pau)) (j (i:)) (dx (t d)) (& (^)) (k>9r (k)) (k>w (k)) (k>l (k)) (p>9r (p)) (p>w (p)) (p>l (p)) (t>9r (t)) (t>w (t)) (t>l (t)) (t>9r<s (t>9r t<s t)) (p>9r<s (p>9r p)) (t<s (t))))) (set! ogi_di_default "pau-h") (set! AccentMaxStart 65) (set! AccentMaxMid 40) (set! AccentMaxEnd 50) (set! AccentQuestion 80) (set! AccentComma2 20) (set! AccentComma3 10) (set! AccentComma4 30) (set! PhraseStart 220) (set! PhraseMid 180) (set! PhraseEnd 140) (set! voicename (quote as_diphone)) (if (string-equal ogi_grouped_or_ungrouped "grouped") (set! ogi_resLPC_analysis_params (list (list (quote dbname) voice_dirname) (list (quote groupfile) (path-append ogi_diphone_dir "group" (string-append voicename "_resLPC.group"))) (quote (data_type "resLPC")) (quote (access_mode "ondemand")))) (set! ogi_resLPC_analysis_params (list (list (quote dbname) voice_dirname) (list (quote unitdic_file) (path-append ogi_diphone_dir "ungrouped" "unittable.ms")) (quote (phoneset "worldbet")) (list (quote base_dir) (path-append ogi_diphone_dir "ungrouped/")) (quote (lpc_dir "lpc/")) (quote (lpc_ext ".lsf")) (quote (exc_dir "lpc/")) (quote (exc_ext ".res")) (quote (pm_dir "pm/")) (quote (pm_ext ".pmv")) (quote (data_type "resLPC")) (quote (access_mode "ondemand")) (quote (samp_freq 22050)) (quote (sig_band 0.01)) (quote (isCompressed "Y")) (quote (preemph 0.96)) (quote (deemphasis 0.99))))) (set! ogi_sinLPC_analysis_params (list (list (quote voicename) voice_dirname) (list (quote groupfile) (path-append ogi_diphone_dir "group" (string-append voicename "_sinLPC.group"))) (quote (access_mode "ondemand")) (quote (useCompressed 0)) (quote (doSinAnalysis 1)))) (if (string-equal ogi_grouped_or_ungrouped "grouped") (set! ogi_sinLPC_analysis_params (append ogi_sinLPC_analysis_params (list (quote (useGrouped 1))))) (set! ogi_sinLPC_analysis_params (append ogi_sinLPC_analysis_params (list (quote (useGrouped 0)) (list (quote unittable_file) (path-append ogi_diphone_dir "ungrouped" "unittable.ms")) (list (quote pmdir) (path-append ogi_diphone_dir "ungrouped" "pm")) (list (quote wavdir) (path-append ogi_diphone_dir "ungrouped" "wav")) (list (quote sinlpcdir) (path-append ogi_diphone_dir "ungrouped" "sinlpc")) (quote (sinlpc_save_format "est_ascii")) (quote (Fs 16000)) (quote (Fvox 4000)) (quote (vuv_filt ((-0.00265023 0.0426373 0.253502 0.413021 0.253502 0.0426373 -0.00265023) (1)))) (quote (lpcorder 14)) (quote (data_type "sinLPC")) (quote (access_mode "ondemand")) (quote (pre-emph 0.95)) (quote (show_chunk_pms 0)))))) (initialize_OGIsynth))>)
   3: (voice_as_diphone)
```
This seems to happen everywhere except with the default, for example, running text2wave without the -eval works fine, but (voice_foo_diphone) breaks, assuming of course foo actually exists. Googling hasn't helped, so, any suggestions?

---

