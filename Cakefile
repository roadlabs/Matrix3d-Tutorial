sys = require 'sys'
fs = require 'fs'
exec = require('child_process').exec
spawn = require('child_process').spawn

task 'watch', 'watches and compiles coffee', ->
  puts "Spawning coffee watcher"
  coffee = spawn 'coffee', ['-cwl', '-o', 'javascripts', 'coffeescripts']

  puts "Spawning sass watcher"
  sass   = spawn 'sass',   ['--watch', 'sass:stylesheets']
  
  [coffee, sass].forEach (child) ->
      child.stdout.on 'data', (data) ->
        sys.print data
        exec "growlnotify -m \"#{data}\" -t \"Cakefile\""
      child.stderr.on 'data', (data) ->
        sys.print data
        exec "growlnotify -m \"#{data}\" -t \"Cakefile\""