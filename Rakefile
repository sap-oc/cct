#!/bin/env rake

require 'bundler/setup'
Bundler.require(:default)

require "rspec/core/rake_task"

RSpec::Core::RakeTask.new(:spec)

Cct.setup(__dir__, verbose: verbose)
Cct.load_tasks!

unless ENV["PACKAGING"] && ENV["PACKAGING"] == "yes"
  require "rspec/core/rake_task"
  RSpec::Core::RakeTask.new(:spec)

  task :syntaxcheck do
    system("for f in `find -name \*.rb`; do echo -n \"Syntaxcheck $f: \"; ruby -c $f || exit $? ; done")
    exit $?.exitstatus
  end

  task default: [
    :syntaxcheck
  ]
end

