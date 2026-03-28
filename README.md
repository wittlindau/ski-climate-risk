# ski-climate-risk

  The global ski industry is a roughly $20 billion industry facing an existential threat from climate change. This interactive dashboard lets you compare how quickly ski conditions are deteriorating across more than 1,200 resorts worldwide.
Using temperature and snowfall data from 1992–2022, each resort is assigned a normalized risk score from 0 to 1 based on the rate at which its local climate is changing — the faster conditions are worsening, the higher the score. The map is built with MapLibre GL JS and deployed as a single self-contained HTML file.

_Data_
  For most of the world — the European Alps, Canadian Rockies, Scandinavia, Japan, and the Appalachians — the model uses ERA5, the industry-standard global climate reanalysis dataset at 9 km resolution. For the American West, ERA5's grid is too coarse to capture the region's extreme topographic variability, so the model instead uses SNOTEL (snow water equivalent) and NOAA's GHCN (temperature) for higher-fidelity ground-truth data.
  Raw data was processed in Python (NumPy, Pandas). Each resort is spatially matched to its nearest station or grid cell, with a 6.5°C/1,000m lapse rate correction applied for elevation differences. Trend slopes for snow and temperature are computed over meteorological winter (Dec–Mar), normalized into a composite score, and exported as embedded GeoJSON.

_A Note on Interpretation_
  This model measures the rate of climatic deterioration, not the current quality of skiing. A score of zero doesn't mean a resort is great — it means its climate hasn't changed much. A high score doesn't mean a resort is closing soon — it means natural conditions are shifting fastest there. Snowmaking infrastructure, funding, and elevation aren't factored in. Think of it as a diagnostic, not a forecast.
