SELECT TOP 100
	p.ApplicantState,
	p.ApplicantName,
	p.ApplicantAddress,
	drs.StateCd as dealer_state,
	d.AppId
	cr.RawXml as carlton_tax_calc,
	cr.ReportDT as carlton_tax_ran
FROM dbo.deal d with(nolock)
INNER JOIN dbo.deals ds with(nolock)
	ON d.AppId = ds.AppId
INNER JOIN dbo.dealers drs with(nolock)
	ON ds.DealerId = drs.DealerId
INNER JOIN dbo.Provenir p with(nolock)
	ON d.DealDetailId = p.ContractDealDetailID
INNER JOIN dbo.customer_reports cr with(nolock)
	ON d.DealDetailId = cr.DealDetailId
	AND cr.SourceSystemCd = 'CARLT'
WHERE d.TypCd = 'C'
	and d.DecisionCd = 'F'
ORDER BY d.AppId DESC
option(recompile)
;
