# pomodoro.el #

The technique is described at http://www.pomodorotechnique.com

## Usage ##

to start the pomodoro you issue `M-x pomodoro`.

In the modeline you will see indicator `W1-25`. This means that you are
working on set 1 and that you have 25 minutes remaining. You'll also get
notification.

The counter will decrease each minutes. When it reaches 0 you will get
notification that it's time to take a break.

The modeline will display `B1-5`, that is you have a break of 5 minutes. When
the count reaches 0 you will get another notification to get back to work and
the set number will increase.

At the end of the 4th set you will get a long break.

The modeline will display `LB` instead of `B`.

Calling `M-x pomodoro` again will reset it to the first working set.

When you don't need the pomodoro anymore you do `M-x pomodoro-stop`. Pomodoro
will finish it's work.

If you got interrupted and you want to rewind the pomodoro on the current set
just do `M-x pomodoro-rewind`.

To skip forward to the start of the next set do `M-x pomodoro-skip-forward`.

Calling `M-x pomodoro-status` will show you notification about current
pomodoro state, time left and set number.

## Installation ##

For status change notifications working you need:

* Libnotify installed
* D-Bus session running
* **notifications.el** (included in GNU Emacs since 24.1)

To activate pomodoro.el simply put it in your load path. For example if you
put the file is in the directory ~/tmp you need to do the following:

``` lisp
(add-to-list 'load-path "~/tmp")
(require 'pomodoro)
```

Alternatively, if you use [el-get](https://github.com/dimitri/el-get) (highly
recommended), use this recipe:

``` lisp
(:name pomodoro
       :type github
       :pkgname "vderyagin/pomodoro.el"
       :post-init (setq pomodoro-icon
                        (expand-file-name "pomodoro/pomodoro_technique.png" el-get-dir)))
```

## Customizing ##

You can customize this mode with the following variables:

`pomodoro-work-duration` - duration (in minutes) of work

`pomodoro-short-break-duration` - duration (in minutes) of short break

`pomodoro-long-break-duration` - duration (in minutes) of long break

`pomodoro-set-number` - number of sets until a long break

`pomodoro-icon` - icon for use in notifications

## Bugs ##

Report bugs on [bugtracker](https://github.com/vderyagin/pomodoro.el/issues).
