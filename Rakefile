require 'rubygems'
require 'points-scraper'
require 'pony'

def send_mail(body, subject)
  Pony.mail({:to => ENV['TO_ADDRESS'],
             :subject => subject,
             :body => body,
             :via => :smtp,
             :via_options => {
               :address => 'smtp.sendgrid.net',
               :port => '587',
               :domain => 'heroku.com',
               :user_name => ENV['SENDGRID_USERNAME'],
               :password => ENV['SENDGRID_PASSWORD'],
               :authentication => :plain,
               :enable_starttls_auto => true}})
end

desc 'getting current TPOINT'
task 'tpoint' do
  require 'points-scraper/tpoint'
  body =
    Points::Scraper::TPoint.new(ENV['TPOINT_USER'], ENV['TPOINT_PASSWORD']).start
  send_mail(body, 'Current TPOINT')
end

desc 'getting current ANA Mileage.'
task 'ana' do
  require 'points-scraper/anamileage'
  body =
    Points::Scraper::AnaMileage.new(ENV['ANA_USER'], ENV['ANA_PASSWORD']).start
  send_mail(body, 'Current ANA Mileage')
end

desc 'getting current Rakuten Points.'
task 'rakuten' do
  require 'points-scraper/rakuten'
  body =
    Points::Scraper::Rakuten.new(ENV['RAKUTEN_USER'], ENV['RAKUTEN_PASSWORD']).start
  send_mail(body, 'Current Rakuten Points')
end
