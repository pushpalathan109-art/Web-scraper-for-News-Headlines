# Web-scraper-for-News-Headlines

def scrape_headlines(url):
    try:
        response = requests.get(url)
        response.raise_for_status()  # Raise error for bad status
        soup = BeautifulSoup(response.text, 'html.parser'
        # This selector depends on the website.
        # For example, for BBC:
        #   headlines = soup.select('h3')
        # For NDTV:
        #   headlines = soup.select('.newsHdng')
        # For Times of India:
        #   headlines = soup.select('span.w_tle')
  headlines = soup.find_all('h3')  # Generic fallback

   cleaned = [h.get_text(strip=True) for h in headlines if h.get_text(strip=True)]
        return cleaned
