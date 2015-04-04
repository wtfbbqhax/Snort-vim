Provide better support for Snort configuration files in VIM. Includes 
 * Fixed syntax highlighting
 * Automatic indentation following a line continuation ('\')
 * Folding of multiline confiugrations (following a line continuation)


To be done: 
 * A better README



    *snort* *hog*                             Improved vim experience for Snort users.

       ____                   _                     __  ~
      / ___| _ __   ___  _ __| |_   ___ ___  _ __  / _| ~
      \___ \| '_ \ / _ \| '__| __| / __/ _ \| '_ \| |_  ~
       ___) | | | | (_) | |  | |_ | (_| (_) | | | |  _| ~
      |____/|_| |_|\___/|_|   \__(_)___\___/|_| |_|_|   ~
                                                       
      Version: ALPHA.1
      Author: Victor Roemer
      Last Changed: March 10, 2013

    ==============================================================================
    CONTENTS                                                          *hog-contents*

        Intro.....................................|hog-intro|
        Syntax....................................|hog-syntax|
        Indentation...............................|hog-indent|
        Navigation................................|hog-navigation|

    ==============================================================================
    INTRO                                                                *hog-intro*

    Note: This is plugin is only a first-pass.

    This plugin aims to improve the experience of modifying Snort configuration
    and rule files with Vim. 

    Provided features
        * Syntax highlighting (compatible with modern versions of Snort)
        * Automatic indentation
        * Navigation mappings

    To make full use of the provided functionality, you'll need the following
    configurations in your |vimrc|.

        set nocompatible
        filetype plugin indent on
        syntax on

    ==============================================================================
    SYNTAX                                                              *hog-syntax*

    This plugin provides syntax highlighting support for modern versions of
    Snort's configurations. 

    TODO: Fill me out!

    Syntax highlighting is defined in the syntax/hog.vim file. 

    ==============================================================================
    INDENTATION                                                         *hog-indent*

    Snort configurations, while usually spanning a single line, can span multiple
    lines with the use of the line-continuation character '\'.

    For example:

        preprocessor stream5_global: \
            track_tcp yes, track_udp no


    Upon encountering a line-continuation character, Snort reads past any whitespace,
    comments, empty lines and lines only containing comments.

    For example, the following configurations are identical:

        preprocessor stream5_global: \ # This is a comment
            #  track_tcp no, track_udp yes
            track_tcp yes, track_udp no

        preprocessor stream5_global: track_tcp yes, track_udp no


    This plugin provides intelligent indentation when encountering line-continuations.

    TODO: Examples!

    ==============================================================================
    NAVIGATION                                                      *hog-navigation*

    The following motions are provided for navigating while in normal mode.

    |]]|                      [count] sections forward or to the next config. 

    |[[|                      [count] sections backward or to the previous config.


    If the matchit plugin is installed (See |matchit-install), the following
    motion is enabled by default:

    |%|                       Find the end of the config line. (This motion spans
                            line-continuations.)
