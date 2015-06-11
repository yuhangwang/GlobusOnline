# GlobusOnline
Globus online file transfer
## How to install and configure Globus Online

* set up globusonline local client by following the "Prerequisites" section this tutorial to upload your ssh key to globus online : https://support.globus.org/entries/30058643-Using-the-Command-Line-Interface-CLI-
Then skip the rest and go to this tutorial to make a new endpoint for your desktop:
https://support.globus.org/entries/24078973

  note 1: don't try the GUI installer which doesn't seem to work even if you have installed Tcllib package.
  I tried and it failed without any error message. 

  note 2: for those who have modified their PYTHONPATH, you may need to unset them to allow the system python work    correctly (otherwise you may get "import site failed" error).
  ```csh
  unsetenv PYTHONHOME
  unsetenv PYTHONPATH
  unsetenv PYTHONROOT
  unsetenv PYTHONBIN
  unsetenv PYTHONLIB
  ```
  and make sure your are suing /use/local/bin/python

* In order to have access to your local scratch directory:

  ```bash
  cd globusconnectpersonal-2.2.0
  ./globusconnect -start -restrict-paths / &
  ssh bob@cli.globusonline.org scp xsede#comet:/oasis/scratch-comet/bob/helloworld.txt  bob#desktop:/Scr/bob/home/
  ./globusconnect -stop
  ```

